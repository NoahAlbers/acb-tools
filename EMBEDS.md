# Webflow embed code — all 15 tools (updated)

Updated 2026-06-13. These replace **Embed block #1** (the iframe) on each `/resources/<tool>` page in Webflow. Leave the JSON-LD schema block alone.

**What changed in every embed:**

- The iframe uses `aria-label` instead of `title`, so the browser no longer shows the lingering hover tooltip (the iframe covers most of the page, so a `title` tooltip never went away).

- The embed forwards the parent page's scroll position into the tool (`sendScroll`), which is what makes the in-tool sticky panels work — an auto-height iframe never scrolls internally, so CSS `position:sticky` alone can't engage.


To update a page: open it in Webflow → find the Embed element holding the iframe → select all → paste the matching block below → publish. The snippets are identical except for `aria-label` and `slug`.


---

## Rental Property ROI Calculator · has a sticky panel

Page: `https://www.advancedcb.com/resources/rental-property-roi-calculator`

```html
<iframe id="acb-tool-frame" aria-label="Rental Property ROI Calculator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='rental-property-roi-calculator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Mortgage Calculator · has a sticky panel

Page: `https://www.advancedcb.com/resources/mortgage-calculator`

```html
<iframe id="acb-tool-frame" aria-label="Mortgage Calculator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='mortgage-calculator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Cap Rate Calculator

Page: `https://www.advancedcb.com/resources/cap-rate-calculator`

```html
<iframe id="acb-tool-frame" aria-label="Cap Rate Calculator"
  style="width:1px;min-width:100%;border:0;height:1400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='cap-rate-calculator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Net Operating Income (NOI) Calculator · has a sticky panel

Page: `https://www.advancedcb.com/resources/net-operating-income-calculator`

```html
<iframe id="acb-tool-frame" aria-label="Net Operating Income (NOI) Calculator"
  style="width:1px;min-width:100%;border:0;height:1700px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='net-operating-income-calculator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Tenant Turnover Cost Calculator · has a sticky panel

Page: `https://www.advancedcb.com/resources/turnover-cost-estimator`

```html
<iframe id="acb-tool-frame" aria-label="Tenant Turnover Cost Calculator"
  style="width:1px;min-width:100%;border:0;height:1900px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='turnover-cost-estimator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## 70% Rule Calculator · has a sticky panel

Page: `https://www.advancedcb.com/resources/70-percent-rule-calculator`

```html
<iframe id="acb-tool-frame" aria-label="70% Rule Calculator"
  style="width:1px;min-width:100%;border:0;height:1400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='70-percent-rule-calculator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Prorated Rent Calculator · has a sticky panel

Page: `https://www.advancedcb.com/resources/prorated-rent-calculator`

```html
<iframe id="acb-tool-frame" aria-label="Prorated Rent Calculator"
  style="width:1px;min-width:100%;border:0;height:1200px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='prorated-rent-calculator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Rent Increase Calculator · has a sticky panel

Page: `https://www.advancedcb.com/resources/rent-increase-calculator`

```html
<iframe id="acb-tool-frame" aria-label="Rent Increase Calculator"
  style="width:1px;min-width:100%;border:0;height:1400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='rent-increase-calculator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Security Deposit Interest Calculator · has a sticky panel

Page: `https://www.advancedcb.com/resources/security-deposit-interest-calculator`

```html
<iframe id="acb-tool-frame" aria-label="Security Deposit Interest Calculator"
  style="width:1px;min-width:100%;border:0;height:1400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='security-deposit-interest-calculator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Lease Agreement Generator · has a sticky panel

Page: `https://www.advancedcb.com/resources/lease-agreement-generator`

```html
<iframe id="acb-tool-frame" aria-label="Lease Agreement Generator"
  style="width:1px;min-width:100%;border:0;height:1200px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='lease-agreement-generator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Rental Application Form Generator

Page: `https://www.advancedcb.com/resources/rental-application-generator`

```html
<iframe id="acb-tool-frame" aria-label="Rental Application Form Generator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='rental-application-generator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Late Rent Notice Generator

Page: `https://www.advancedcb.com/resources/late-rent-notice-generator`

```html
<iframe id="acb-tool-frame" aria-label="Late Rent Notice Generator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='late-rent-notice-generator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Security Deposit Return Letter Generator

Page: `https://www.advancedcb.com/resources/security-deposit-return-letter-generator`

```html
<iframe id="acb-tool-frame" aria-label="Security Deposit Return Letter Generator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='security-deposit-return-letter-generator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Rent Increase Notice Generator

Page: `https://www.advancedcb.com/resources/rent-increase-notice-generator`

```html
<iframe id="acb-tool-frame" aria-label="Rent Increase Notice Generator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='rent-increase-notice-generator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```


---

## Move-In / Move-Out Checklist Creator

Page: `https://www.advancedcb.com/resources/move-in-move-out-checklist-creator`

```html
<iframe id="acb-tool-frame" aria-label="Move-In / Move-Out Checklist Creator"
  style="width:1px;min-width:100%;border:0;height:1200px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='move-in-move-out-checklist-creator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```
