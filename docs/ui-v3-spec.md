# UI v3 spec — cross-cutting polish pass

Applies to every tool. Copy code verbatim; adjust slugs. The canonical implementation lives in
`tools/cap-rate-calculator/index.html` (components) — check it when in doubt.

## 1. Badges (subtle, non-clickable)

Replace `.badge` CSS everywhere with:
```css
.badge{font-size:12px;font-weight:500;color:#7E88B8;background:rgba(61,90,241,.045);border:1px solid rgba(61,90,241,.10);border-radius:50px;padding:4px 12px;letter-spacing:.01em}
```

## 2. Rolling numbers (tween every displayed result)

Add once per tool; use for hero numbers and stat values (anything numeric that changes on input).
```js
var ACB_REDUCED=window.matchMedia&&matchMedia('(prefers-reduced-motion: reduce)').matches;
function tweenText(el,fmt,to,ms){
  if(!el)return;
  if(ACB_REDUCED||!isFinite(to)){el.textContent=fmt(to);el.__tv=isFinite(to)?to:0;return;}
  var from=isFinite(el.__tv)?el.__tv:0;
  el.__tv=to;
  if(from===to){el.textContent=fmt(to);return;}
  var t0=performance.now();ms=ms||480;
  (function step(t){
    var p=Math.min(1,((t||performance.now())-t0)/ms);p=1-Math.pow(1-p,3);
    el.textContent=fmt(from+(to-from)*p);
    if(p<1)requestAnimationFrame(step);
  })(t0);
}
```
Pattern: where code does `el.textContent=fmtUSD(x)`, use `tweenText(el,function(v){return fmtUSD(v);},x)`.
Percent: `tweenText(el,function(v){return v.toFixed(2)+'%';},x)`. For stat rows rebuilt via innerHTML,
either switch to keyed updates or tween at least the hero numbers — hero numbers are mandatory.

## 3. Calendar date picker (all date inputs)

Replace direct `<input type="date">` UX with this popover (input stays `type="date"` for value
semantics; picker writes ISO + dispatches `input`). Add CSS+JS once, then `acbDate(el)` each input.
```css
.acb-cal{position:absolute;z-index:120;background:#fff;border:1px solid var(--acb-border);border-radius:14px;box-shadow:0 12px 32px rgba(26,26,46,.14);padding:14px;width:264px;font-family:inherit}
.acb-cal-head{display:flex;align-items:center;justify-content:space-between;margin-bottom:8px}
.acb-cal-title{font-weight:700;font-size:14px}
.acb-cal-nav{width:30px;height:30px;border:1px solid var(--acb-border);background:#fff;border-radius:8px;cursor:pointer;color:var(--acb-text-mid);font-size:14px}
.acb-cal-nav:hover{border-color:var(--acb-blue);color:var(--acb-blue)}
.acb-cal-grid{display:grid;grid-template-columns:repeat(7,1fr);gap:2px;text-align:center}
.acb-cal-dow{font-size:10.5px;font-weight:700;color:var(--acb-text-light);padding:4px 0;text-transform:uppercase}
.acb-cal-d{border:none;background:none;border-radius:8px;padding:7px 0;font-size:13px;font-family:inherit;cursor:pointer;color:var(--acb-text)}
.acb-cal-d:hover{background:var(--acb-blue-light)}
.acb-cal-d.out{color:#C9CDDC}
.acb-cal-d.today{box-shadow:inset 0 0 0 1.5px var(--acb-blue-mid)}
.acb-cal-d.sel{background:var(--acb-blue);color:#fff;font-weight:700}
.acb-cal-foot{display:flex;justify-content:space-between;margin-top:8px}
.acb-cal-foot button{border:none;background:none;color:var(--acb-blue);font-weight:600;font-size:12.5px;cursor:pointer;font-family:inherit;padding:4px 6px}
```
```js
function acbDate(input){
  var pop=null,view;
  function iso(d){return d.getFullYear()+'-'+String(d.getMonth()+1).padStart(2,'0')+'-'+String(d.getDate()).padStart(2,'0');}
  function close(){if(pop){pop.remove();pop=null;document.removeEventListener('mousedown',onDoc);}}
  function onDoc(e){if(pop&&!pop.contains(e.target)&&e.target!==input)close();}
  function set(d){input.value=iso(d);input.dispatchEvent(new Event('input',{bubbles:true}));input.dispatchEvent(new Event('change',{bubbles:true}));close();}
  function render(){
    var sel=input.value?new Date(input.value+'T00:00:00'):null;
    var today=new Date();today.setHours(0,0,0,0);
    var y=view.getFullYear(),m=view.getMonth();
    var first=new Date(y,m,1),startDow=first.getDay(),dim=new Date(y,m+1,0).getDate();
    var h='<div class="acb-cal-head"><button type="button" class="acb-cal-nav" data-n="-1" aria-label="Previous month">‹</button><span class="acb-cal-title">'+view.toLocaleDateString('en-US',{month:'long',year:'numeric'})+'</span><button type="button" class="acb-cal-nav" data-n="1" aria-label="Next month">›</button></div><div class="acb-cal-grid">';
    ['Su','Mo','Tu','We','Th','Fr','Sa'].forEach(function(d){h+='<span class="acb-cal-dow">'+d+'</span>';});
    var prev=new Date(y,m,0).getDate();
    for(var i=0;i<startDow;i++)h+='<button type="button" class="acb-cal-d out" data-d="'+iso(new Date(y,m-1,prev-startDow+1+i))+'">'+(prev-startDow+1+i)+'</button>';
    for(var d=1;d<=dim;d++){
      var cur=new Date(y,m,d),cls='acb-cal-d';
      if(sel&&cur.getTime()===sel.getTime())cls+=' sel';
      if(cur.getTime()===today.getTime())cls+=' today';
      h+='<button type="button" class="'+cls+'" data-d="'+iso(cur)+'">'+d+'</button>';
    }
    var cells=startDow+dim,next=1;
    for(var j=cells;j%7!==0;j++)h+='<button type="button" class="acb-cal-d out" data-d="'+iso(new Date(y,m+1,next))+'">'+(next++)+'</button>';
    h+='</div><div class="acb-cal-foot"><button type="button" data-t="1">Today</button><button type="button" data-c="1">Close</button></div>';
    pop.innerHTML=h;
    pop.querySelectorAll('[data-n]').forEach(function(b){b.addEventListener('click',function(e){e.stopPropagation();view.setMonth(view.getMonth()+(+b.dataset.n));render();});});
    pop.querySelectorAll('[data-d]').forEach(function(b){b.addEventListener('click',function(){set(new Date(b.dataset.d+'T00:00:00'));});});
    pop.querySelector('[data-t]').addEventListener('click',function(){set(new Date());});
    pop.querySelector('[data-c]').addEventListener('click',close);
  }
  function open(){
    if(pop)return;
    view=input.value?new Date(input.value+'T00:00:00'):new Date();view.setDate(1);
    pop=document.createElement('div');pop.className='acb-cal';
    var r=input.getBoundingClientRect();
    var wrap=input.closest('.field')||input.parentNode;
    if(getComputedStyle(wrap).position==='static')wrap.style.position='relative';
    wrap.appendChild(pop);
    pop.style.top=(input.offsetTop+input.offsetHeight+6)+'px';
    pop.style.left=Math.max(0,Math.min(input.offsetLeft,wrap.clientWidth-270))+'px';
    render();
    setTimeout(function(){document.addEventListener('mousedown',onDoc);},0);
  }
  input.addEventListener('click',function(e){e.preventDefault();open();});
  input.addEventListener('keydown',function(e){if(e.key==='Enter'||e.key===' '){e.preventDefault();open();}if(e.key==='Escape')close();});
}
```
Apply: `document.querySelectorAll('input[type=date]').forEach(acbDate);` after render (and re-apply
after any rerender that recreates date inputs).

## 4. Tooltips v2 (richer)

New markup (title attribute drives the bold heading):
```html
<span class="acb-tip" tabindex="0" data-t="Cap rate"><svg .../><span class="acb-tip-bubble"><b></b><i>Body text…</i></span></span>
```
CSS replaces the old `.acb-tip-bubble` rules:
```css
.acb-tip{position:relative;display:inline-flex;color:var(--acb-text-light);cursor:help;vertical-align:middle;margin-left:5px}
.acb-tip:hover,.acb-tip:focus,.acb-tip.open{color:var(--acb-blue)}
.acb-tip-bubble{position:absolute;bottom:calc(100% + 10px);left:50%;transform:translateX(-50%) translateY(4px);background:#fff;color:var(--acb-text-mid);border:1px solid var(--acb-border);box-shadow:0 10px 30px rgba(26,26,46,.14);font-size:12.5px;font-weight:400;line-height:1.6;padding:12px 14px;border-radius:12px;width:270px;opacity:0;pointer-events:none;transition:opacity .18s,transform .18s;z-index:60;text-transform:none;letter-spacing:normal;text-align:left}
.acb-tip-bubble::after{content:"";position:absolute;top:100%;left:50%;transform:translateX(-50%);border:7px solid transparent;border-top-color:#fff;filter:drop-shadow(0 1.5px 0 var(--acb-border))}
.acb-tip-bubble b{display:block;font-size:12px;font-weight:700;color:var(--acb-blue);text-transform:uppercase;letter-spacing:.06em;margin-bottom:5px}
.acb-tip-bubble i{font-style:normal;display:block}
.acb-tip:hover .acb-tip-bubble,.acb-tip:focus .acb-tip-bubble,.acb-tip.open .acb-tip-bubble{opacity:1;transform:translateX(-50%) translateY(0)}
@media (max-width:720px){.acb-tip-bubble{left:auto;right:-12px;transform:none}.acb-tip:hover .acb-tip-bubble,.acb-tip:focus .acb-tip-bubble,.acb-tip.open .acb-tip-bubble{transform:none}.acb-tip-bubble::after{left:auto;right:14px;transform:none}}
```
JS once per tool (fills titles + tap-to-toggle):
```js
document.querySelectorAll('.acb-tip').forEach(function(t){
  var b=t.querySelector('.acb-tip-bubble b');
  if(b&&!b.textContent)b.textContent=t.dataset.t||'';
  t.addEventListener('click',function(e){e.stopPropagation();t.classList.toggle('open');});
});
document.addEventListener('click',function(){document.querySelectorAll('.acb-tip.open').forEach(function(t){t.classList.remove('open');});});
```
When migrating existing tooltips, wrap the body in `<b></b><i>old text</i>` and set `data-t` to the
term being explained (e.g. the field label).

## 5. First-run coach mark

Once per tool ever. Pulsing ring on the primary input + a bubble saying what to do. Dismiss on
"Got it", Escape, or the first real input anywhere.
```css
.acb-coach-ring{position:relative;z-index:91}
.acb-coach-ring::after{content:"";position:absolute;inset:-6px;border-radius:14px;border:2px solid var(--acb-blue);animation:acbPulse 1.6s ease-out infinite;pointer-events:none}
@keyframes acbPulse{0%{opacity:.9;transform:scale(.985)}70%{opacity:0;transform:scale(1.035)}100%{opacity:0}}
.acb-coach{position:absolute;z-index:92;background:var(--acb-text);color:#fff;border-radius:12px;padding:13px 16px;font-size:13.5px;line-height:1.55;width:250px;box-shadow:0 12px 32px rgba(26,26,46,.3)}
.acb-coach::before{content:"";position:absolute;bottom:100%;left:24px;border:8px solid transparent;border-bottom-color:var(--acb-text)}
.acb-coach b{display:block;margin-bottom:3px}
.acb-coach button{margin-top:9px;background:#fff;color:var(--acb-text);border:none;border-radius:50px;padding:6px 16px;font-weight:700;font-size:12.5px;cursor:pointer;font-family:inherit}
```
```js
function acbCoach(slug,target,title,body){
  try{if(localStorage.getItem('acb:'+slug+':coached'))return;}catch(e){return;}
  var el=typeof target==='string'?document.querySelector(target):target;
  if(!el)return;
  function done(){try{localStorage.setItem('acb:'+slug+':coached','1');}catch(e){}
    el.classList.remove('acb-coach-ring');if(tip)tip.remove();
    document.removeEventListener('input',done,true);}
  el.classList.add('acb-coach-ring');
  var wrap=el.closest('.field')||el.parentNode;
  if(getComputedStyle(wrap).position==='static')wrap.style.position='relative';
  var tip=document.createElement('div');tip.className='acb-coach';
  tip.innerHTML='<b>'+title+'</b>'+body+'<br><button type="button">Got it</button>';
  wrap.appendChild(tip);
  tip.style.top=(el.offsetTop+el.offsetHeight+12)+'px';
  tip.style.left=Math.max(0,Math.min(el.offsetLeft,wrap.clientWidth-260))+'px';
  tip.querySelector('button').addEventListener('click',done);
  document.addEventListener('input',done,true);
  document.addEventListener('keydown',function esc(e){if(e.key==='Escape'){done();document.removeEventListener('keydown',esc);}});
}
```
Call after initial render, e.g.
`acbCoach('cap-rate-calculator','#price','Start here','Enter the property’s price — results update live as you type.');`
Wizards: point at the first meaningful control of step 1. Builders: the first setup field.

## 6. Rating prompt (engagement-triggered) + working ratings

After **120 s on page AND ≥6 clicks**, show a centered modal asking for a rating — once ever per
tool (`acb:<slug>:ratePrompted`), and never if the user already rated (`acb:<slug>:rating`).
Voting in the modal reuses the existing vote path (updates the visible aggregate + POSTs to
FormSubmit). Seeds must stay within **100–800** and 4.5–4.9 (lease was 853 → change to **784**
in BOTH the widget seed and the kit JSON-LD).
```css
.acb-rate-pop{position:fixed;inset:0;background:rgba(26,26,46,.45);z-index:200;display:flex;align-items:center;justify-content:center;padding:20px}
.acb-rate-card{background:#fff;border-radius:18px;padding:30px 34px;max-width:380px;text-align:center;box-shadow:0 24px 64px rgba(26,26,46,.3)}
.acb-rate-card h3{font-size:19px;font-weight:800;margin-bottom:6px}
.acb-rate-card p{font-size:13.5px;color:var(--acb-text-mid);line-height:1.55;margin-bottom:12px}
.acb-rate-card .skip{margin-top:10px;background:none;border:none;color:var(--acb-text-light);font-size:12.5px;cursor:pointer;font-family:inherit;text-decoration:underline}
```
```js
(function(){
  var SLUG='TOOL_SLUG',clicks=0,shown=false,t0=Date.now();
  try{if(localStorage.getItem('acb:'+SLUG+':ratePrompted')||localStorage.getItem('acb:'+SLUG+':rating'))return;}catch(e){return;}
  document.addEventListener('click',function(){clicks++;maybe();});
  setTimeout(maybe,121000);
  function maybe(){
    if(shown||clicks<6||Date.now()-t0<120000)return;
    shown=true;
    try{localStorage.setItem('acb:'+SLUG+':ratePrompted','1');}catch(e){}
    var pop=document.createElement('div');pop.className='acb-rate-pop';
    pop.innerHTML='<div class="acb-rate-card"><h3>Quick favor?</h3><p>If this tool saved you time, a rating helps other landlords find it.</p><div class="acb-rate-stars" style="font-size:34px"></div><button type="button" class="skip">Maybe later</button></div>';
    document.body.appendChild(pop);
    var stars=pop.querySelector('.acb-rate-stars');
    for(var i=1;i<=5;i++)(function(i){
      var b=document.createElement('button');b.type='button';b.className='acb-star';b.textContent='★';b.style.fontSize='34px';
      b.onmouseenter=function(){[].forEach.call(stars.children,function(s,j){s.classList.toggle('on',j<i);});};
      b.onclick=function(){
        var w=document.querySelectorAll('#acbStars .acb-star')[i-1];
        if(w)w.click(); /* routes through the real vote path */
        pop.querySelector('.acb-rate-card').innerHTML='<h3>Thank you! ⭐</h3><p>Your rating was recorded.</p>';
        setTimeout(function(){pop.remove();},1400);
      };
      stars.appendChild(b);
    })(i);
    pop.querySelector('.skip').addEventListener('click',function(){pop.remove();});
    pop.addEventListener('click',function(e){if(e.target===pop)pop.remove();});
  }
})();
```

## 7. Smooth size changes

```js
function smoothResize(el,mutate){
  if(ACB_REDUCED||!el){if(mutate)mutate();return;}
  var h0=el.offsetHeight;mutate();var h1=el.offsetHeight;
  if(Math.abs(h0-h1)<3)return;
  el.style.height=h0+'px';el.style.overflow='hidden';el.style.transition='height .3s ease';
  void el.offsetHeight;
  el.style.height=h1+'px';
  setTimeout(function(){el.style.height='';el.style.overflow='';el.style.transition='';},320);
}
```
Wrap mutations that change a card/section's height (mode switches, expanding panels, result blocks
that appear/disappear). Don't wrap per-keystroke recomputes of same-size text.

## 8. Layout: one input card, sections inside; results-first; mini chart in first viewport

- Merge multiple input cards into ONE `.card` with internal section headers:
  ```css
  .sec-divider{display:flex;align-items:center;gap:8px;margin:22px 0 12px;padding-top:18px;border-top:1px solid var(--acb-border);font-size:12px;font-weight:700;letter-spacing:.08em;text-transform:uppercase;color:var(--acb-text-light)}
  .sec-divider:first-child{margin-top:0;padding-top:0;border-top:none}
  .sec-divider svg{width:15px;height:15px;color:var(--acb-blue)}
  ```
  (first section header has no divider line).
- Desktop: results column `position:sticky;top:16px` so hero stays in view while scrolling inputs.
- If the tool has charts: a compact live chart (~120–150px tall) must sit in the results column
  directly under the hero numbers (visible in the first viewport). Big detailed charts/tables stay
  below.
- Order content by importance: hero → mini chart → key stats → secondary panels → tables.

## 9. Icons

Inline stroke SVGs only (viewBox 0 0 24 24, fill none, stroke currentColor, stroke-width 2,
round caps/joins). Standard set (path data) — copy as needed:
- home: `M3 10.5 12 3l9 7.5M5 9.5V21h14V9.5` + `M9 21v-6h6v6`
- doc: `M14 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V8z` + `M14 2v6h6`
- calc: `rect x4 y2 w16 h20 rx2` + `M8 6h8M8 10h2M12 10h2M16 10h2M8 14h2M12 14h2M16 14h2M8 18h2M12 18h6`
- dollar: `M12 1v22` + `M17 5H9.5a3.5 3.5 0 0 0 0 7h5a3.5 3.5 0 0 1 0 7H6`
- trend: `M23 6l-9.5 9.5-5-5L1 18` + `M17 6h6v6`
- percent: `line 19,5 5,19` + `circle 6.5,6.5 r2.5` + `circle 17.5,17.5 r2.5`
- key: `M21 2l-2 2m-7.6 7.6a5.5 5.5 0 1 1-7.78 7.78 5.5 5.5 0 0 1 7.78-7.78zm0 0L15.5 7.5m3 3L21 8m-3-3 3 3`
- clipboard-check: `M16 4h2a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2H6a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h2` + `rect x8 y2 w8 h4 rx1` + `M9 13l2 2 4-4`
- mail: `rect x2 y4 w20 h16 rx2` + `M22 6l-10 7L2 6`
- shield: `M12 22s8-4 8-10V5l-8-3-8 3v7c0 6 8 10 8 10z`
- calendar: `rect x3 y4 w18 h18 rx2` + `M16 2v4M8 2v4M3 10h18`
- search: `circle 11,11 r8` + `M21 21l-4.35-4.35`
Use them in hub cards and `.sec-divider` headers. Never emoji for UI chrome (emoji okay inside
document content like the checklist share modal).

## 10. Printable documents (lease, application, late-rent, deposit-return, rent-increase-notice, checklist PDF)

- **Footer (in the document itself):** first line, normal size:
  `This [Lease Agreement] was created with Advanced Collection Bureau, Inc. (advancedcb.com)`
  then in smaller text the legal line, doc-adapted:
  `This resource from Advanced Collection Bureau, Inc. is for general informational purposes. It is not legal advice. [DOC-SPECIFIC: e.g. "Rent increase rules vary by state, county, and city — rent control ordinances add caps and procedures —"] and laws change; verify current requirements with a local attorney before [using/sending] it.`
- **Two separate buttons:** `Print` (window.print) and `Download PDF` (direct .pdf download —
  no print dialog). Replace any "Print / Save as PDF" combined button.
- **Download PDF = pre-filled fillable AcroForm** via pdf-lib (unpkg, already used by lease/
  application): every blank in the PDF is an editable TextField/CheckBox **pre-filled** from the
  tool's current answers (`field.setText(value)`, checkboxes checked to match). Tools that already
  generate blank fillable PDFs: reuse the generator, fill from state. Tools without pdf-lib yet
  (notices): add the CDN tag and build a compact 1–2 page form-letter PDF with pre-filled fields.
  Filename pattern stays `<Doc>-<ST>.pdf`.

## 11. Hub page (`index.html` at repo root)

Search box (filters name+description+keywords, case-insensitive, instant) + category dropdown:
All · Calculators · Documents & Notices · Inspections & Checklists. Cards get icons. "No results"
empty state with a clear-search link.

## 12. Rating seeds (final, all within 100–800)

lease 4.9/**784** (changed) · application 4.8/294 · late-rent 4.9/391 · deposit-return 4.8/227 ·
rent-increase-notice 4.8/189 · roi 4.9/487 · mortgage 4.8/641 · cap-rate 4.8/312 · noi 4.7/203 ·
turnover 4.9/158 · 70% 4.8/176 · checklist 4.9/512 · prorated 4.8/426 · rent-increase-calc
4.7/284 · deposit-interest 4.8/341. Widget seed and kit JSON-LD must match exactly.

## 13. Tool-specific fixes in this pass

- **ROI:** the "Use a loan?" toggle renders on top of its label — replace with a proper switch
  (visually distinct track+knob, label left, switch right, never overlapping):
  ```css
  .switch{position:relative;width:46px;height:26px;background:#D0D3DC;border-radius:50px;border:none;cursor:pointer;transition:background .25s;flex-shrink:0;padding:0}
  .switch.on{background:var(--acb-blue)}
  .switch::after{content:"";position:absolute;top:3px;left:3px;width:20px;height:20px;background:#fff;border-radius:50%;transition:transform .25s;box-shadow:0 1px 3px rgba(0,0,0,.25)}
  .switch.on::after{transform:translateX(20px)}
  .switch-row{display:flex;align-items:center;justify-content:space-between;gap:12px}
  ```
  Use this switch for ALL boolean toggles across tools (replace chip pairs only where the control
  is a true on/off, not a choice).
- **ROI:** 4 input cards → 1 card with `.sec-divider` sections (Purchase · Income · Expenses ·
  Sale); compact live donut at top of the sticky results column.
