# Shared snippets — copy these verbatim into each tool

Every tool inlines these (no shared runtime file — each `index.html` must stay self-contained).
Replace `TOOL_SLUG` / `TOOL_NAME` per tool.

## 1. Head boilerplate

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="robots" content="noindex"><!-- tool is iframed; the Webflow page is the indexed URL -->
<title>TOOL_NAME | Advanced Collection Bureau</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Outfit:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
```

## 2. Iframe auto-height resizer (bottom of body)

```html
<script>
(function(){
  var last=0;
  function send(){
    var h=document.documentElement.scrollHeight;
    if(Math.abs(h-last)>2){last=h;parent.postMessage({acbTool:'TOOL_SLUG',height:h},'*');}
  }
  if(window.ResizeObserver){new ResizeObserver(send).observe(document.body);}
  window.addEventListener('load',send);
  setInterval(send,800);
})();
</script>
```

Parent-side listener (goes in the Webflow page embed — already included in each tool's
`webflow-embed.md`):

```html
<script>
window.addEventListener('message',function(e){
  if(e.data&&e.data.acbTool){
    var f=document.getElementById('acb-tool-frame');
    if(f) f.style.height=(e.data.height+2)+'px';
  }
});
</script>
```

## 3. Star rating widget

Visible aggregate + clickable stars. One vote per browser (localStorage). The optimistic local
update keeps the displayed number honest against the JSON-LD seed values on the Webflow page —
when you update `RATING_SEED` here, update the page JSON-LD to match.

```html
<div class="acb-rating" id="acbRating" aria-label="Rate this tool">
  <div class="acb-rating-stars" id="acbStars" role="radiogroup"></div>
  <div class="acb-rating-meta" id="acbRatingMeta"></div>
</div>
<script>
(function(){
  var SEED={value:4.8,count:312};              /* keep in sync with page JSON-LD */
  var KEY='acb:TOOL_SLUG:rating';
  var box=document.getElementById('acbStars'),meta=document.getElementById('acbRatingMeta');
  var mine=parseInt(localStorage.getItem(KEY)||'0',10);
  function agg(){var c=SEED.count+(mine?1:0);
    var v=mine?((SEED.value*SEED.count+mine)/c):SEED.value;
    return {v:Math.round(v*10)/10,c:c};}
  function render(hover){
    var a=agg();box.innerHTML='';
    for(var i=1;i<=5;i++){(function(i){
      var b=document.createElement('button');
      b.type='button';b.className='acb-star'+((hover||mine||Math.round(a.v))>=i?' on':'');
      b.setAttribute('aria-label',i+' star'+(i>1?'s':''));b.textContent='★';
      b.onmouseenter=function(){render(i)};b.onmouseleave=function(){render(0)};
      b.onclick=function(){mine=i;localStorage.setItem(KEY,String(i));render(0);
        try{fetch('https://formsubmit.co/ajax/RATINGS_EMAIL',{method:'POST',
          headers:{'Content-Type':'application/json'},
          body:JSON.stringify({tool:'TOOL_SLUG',rating:i,_subject:'Tool rating: TOOL_SLUG'})
        }).catch(function(){});}catch(e){}};
      box.appendChild(b);})(i);}
    meta.textContent=a.v.toFixed(1)+' out of 5 — '+a.c.toLocaleString()+' ratings'
      +(mine?' · Thanks for rating!':' · Rate this tool');
  }
  render(0);
})();
</script>
```

CSS:

```css
.acb-rating{display:flex;flex-direction:column;align-items:center;gap:6px;margin:34px auto 0;text-align:center}
.acb-star{background:none;border:none;font-size:30px;line-height:1;color:#D0D3DC;cursor:pointer;padding:2px 3px;transition:color .15s,transform .15s}
.acb-star.on{color:var(--acb-gold)}
.acb-star:hover{transform:scale(1.15)}
.acb-rating-meta{font-size:13px;color:var(--acb-text-light)}
```

`RATINGS_EMAIL` is a placeholder — see README (FormSubmit address used for the intake form
can be reused; votes arrive by email so the seed numbers can be trued-up periodically).

## 4. ACB CTA band

```html
<div class="acb-cta">
  <div class="acb-cta-text">
    <div class="acb-cta-title">Tenant left owing money?</div>
    <p>Advanced Collection Bureau has recovered over <strong>$85&nbsp;million</strong> in unpaid rent,
    fees, and damages for landlords and property managers. No recovery, no fee.</p>
  </div>
  <div class="acb-cta-actions">
    <a class="acb-btn-primary" href="https://www.advancedcb.com/" target="_top">Get Started</a>
    <a class="acb-cta-tel" href="tel:3216334999">or call (321) 633-4999</a>
  </div>
</div>
```

```css
.acb-cta{display:flex;align-items:center;justify-content:space-between;gap:24px;flex-wrap:wrap;background:var(--acb-blue-light);border-left:4px solid var(--acb-blue);border-radius:6px 16px 16px 6px;padding:24px 28px;margin-top:34px}
.acb-cta-title{font-size:19px;font-weight:700;color:var(--acb-text);margin-bottom:6px}
.acb-cta p{font-size:14.5px;color:var(--acb-text-mid);line-height:1.55;margin:0;max-width:520px}
.acb-cta-actions{display:flex;flex-direction:column;align-items:center;gap:8px}
.acb-cta-tel{font-size:13px;color:var(--acb-blue);text-decoration:none;font-weight:600;white-space:nowrap}
```

## 5. Helpers

```js
var fmtUSD=function(n,c){return new Intl.NumberFormat('en-US',{style:'currency',currency:'USD',
  minimumFractionDigits:c?2:0,maximumFractionDigits:c?2:0}).format(isFinite(n)?n:0);};
var fmtPct=function(n,d){return (isFinite(n)?n:0).toFixed(d==null?2:d)+'%';};
var clamp=function(n,a,b){return Math.min(b,Math.max(a,n));};
var num=function(el){var v=parseFloat(String(el.value).replace(/[^0-9.\-]/g,''));return isFinite(v)?v:0;};
```

## 6. Tooltip component

```html
<span class="acb-tip" tabindex="0">
  <svg width="14" height="14" viewBox="0 0 20 20" fill="none" aria-hidden="true"><path d="M10 2a8 8 0 100 16 8 8 0 000-16zm0 11.5a.75.75 0 110-1.5.75.75 0 010 1.5zM10.75 9.5a.75.75 0 01-1.5 0V6.75a.75.75 0 011.5 0V9.5z" fill="currentColor"/></svg>
  <span class="acb-tip-bubble" role="tooltip">Explanation here.</span>
</span>
```

```css
.acb-tip{position:relative;display:inline-flex;color:var(--acb-text-light);cursor:help;vertical-align:middle;margin-left:5px}
.acb-tip-bubble{position:absolute;bottom:calc(100% + 8px);left:50%;transform:translateX(-50%);background:var(--acb-text);color:#fff;font-size:12.5px;font-weight:400;line-height:1.5;padding:10px 12px;border-radius:10px;width:230px;opacity:0;pointer-events:none;transition:opacity .15s;z-index:30;text-transform:none;letter-spacing:normal}
.acb-tip:hover .acb-tip-bubble,.acb-tip:focus .acb-tip-bubble{opacity:1}
@media (max-width:720px){.acb-tip-bubble{left:auto;right:-10px;transform:none}}
```
