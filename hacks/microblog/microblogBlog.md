---
layout: post
title: "Submodule 4"
description: "Submodule 4 of AI Usage Mini-Quest"
permalink: /digital-famine/microblog/microb/
parent: "AI Usage"
team: "Thinkers"
submodule: 4
categories: [CSP, Submodule, Microblogging]
tags: [microblogging, submodule, unzippers]
author: "Nicolas Diaz"
date: 2025-10-21
breadcrumb: true
---

<div style="font-family:system-ui, -apple-system, 'Segoe UI', Roboto, 'Helvetica Neue', Arial; color:#e0e0e0; line-height:1.45; background:#0f111a; padding:20px;">

  <!-- Microblog Overview -->
  <section style="max-width:900px; margin:0 auto 28px; padding:18px; background:#27293d; border-radius:10px; box-shadow:0 6px 18px rgba(0,0,0,0.5);">
    <h1 style="margin:0 0 8px 0; font-size:1.6rem; color:#f3f4f6;">Submodule 4</h1>
    <h2 style="margin:0 0 12px 0; font-size:1.15rem; color:#a5b4fc;">Microblogging System Overview</h2>
    <h3 style="margin-top:6px; color:#cbd5e1;">What is the Microblog Feature?</h3>
    <p>Microblogging allows **lightweight, short-form communication** on a specific page. Users can post thoughts, questions, announcements, or opinions quickly without leaving the page. Using a floating <strong>💬 Microblog</strong> button, a side panel slides in with **real-time updates**, post creation, replies, and reactions. Microblogs are like mini-discussion threads, ideal for fast collaboration or micro-updates.</p>

    <h3 style="margin-top:8px; color:#cbd5e1;">Why Use Microblogs?</h3>
    <ul>
      <li>Encourage rapid user interaction and feedback.</li>
      <li>Keep discussions page-specific and contextual.</li>
      <li>Provide real-time updates on announcements or questions.</li>
      <li>Enable structured data collection for analytics.</li>
    </ul>

    <h3 style="margin-top:8px; color:#cbd5e1;">Key Components</h3>
    <h4 style="margin:8px 0 4px 0; color:#f3f4f6;">1. User Interface</h4>
    <ul>
      <li>Floating Microblog button 💬</li>
      <li>Slide-in side panel for reading and writing posts</li>
      <li>Responsive layout for desktop and mobile</li>
      <li>Inline editor for post creation and editing</li>
      <li>Reactions (like 👍, ❤️) and threaded replies</li>
    </ul>

    <h4 style="margin:8px 0 4px 0; color:#f3f4f6;">2. Architecture</h4>
    <p>The feature uses three coordinated layers:</p>
    <strong style="color:#a5b4fc;">Layout Layer</strong> (<code>_layouts/opencs.html</code>)
    <ul>
      <li>Loads Tailwind / jQuery and renders the button & panel</li>
    </ul>
    <strong style="color:#a5b4fc;">JavaScript Layer</strong> (<code>assets/js/api/microblog.js</code>)
    <ul>
      <li>Handles UI state, real-time updates, drag/drop, and API calls</li>
    </ul>
    <strong style="color:#a5b4fc;">Backend Layer</strong>
    <ul>
      <li><code>GET /microblog</code> — fetch posts</li>
      <li><code>POST /microblog</code> — create post</li>
      <li><code>POST /microblog/reply</code> — add reply</li>
      <li><code>POST /microblog/reaction</code> — react to a post</li>
    </ul>

    <h3 style="margin-top:8px; color:#cbd5e1;">Enabling Microblogs</h3>
    <pre style="background:#111827; color:#f3f4f6; padding:10px; border-radius:6px; overflow:auto;">
---
layout: post
microblog: True
title: Your Title
description: Your Description
permalink: /your-path
---
    </pre>

    <h3 style="margin-top:8px; color:#cbd5e1;">Features & APCSP Requirements</h3>
    <ul>
      <li>Create, edit, and reply to posts</li>
      <li>React with emojis</li>
      <li>Real-time page-scoped & site-wide updates</li>
      <li>Persistent progress using local storage or API/database</li>
      <li>Student-developed procedure with sequencing, selection, and iteration</li>
      <li>Use of a JSON list collection to store posts and manage program complexity</li>
      <li>Input: user actions (drag/drop, keyboard, button), device input, or online data</li>
      <li>Output: visual feedback (score, highlight, alerts)</li>
    </ul>
  </section>

  <!-- Game Section -->
  <section id="post-sorter-section" style="max-width:950px; margin:0 auto; padding:20px; background:#1e1f2a; border-radius:12px; box-shadow:0 8px 24px rgba(0,0,0,0.5);">
    <h2 style="margin-top:0; color:#fff;">🎯 Post Sorter Challenge</h2>

    <!-- Score and Restart -->
    <div style="display:flex; gap:20px; align-items:center; margin-bottom:16px;">
      <div style="font-weight:600; color:#cbd5e1;">Score: <span id="ps-score">0</span></div>
      <div style="font-weight:600; color:#cbd5e1;">Mistakes: <span id="ps-mistakes">0</span></div>
      <button id="ps-restart" style="margin-left:auto; padding:10px 16px; border-radius:8px; border:0; background:#3b82f6; color:#fff; cursor:pointer; font-weight:600;">Restart Round</button>
    </div>

    <!-- Game Layout -->
    <div style="display:flex; gap:20px; flex-wrap:wrap; align-items:flex-start;">
      <!-- Post Display -->
      <div id="ps-play-area" aria-live="polite" style="flex:1 1 350px; min-height:180px; border-radius:12px; border:2px dashed #374151; padding:16px; background:#11121a;">
        <div style="color:#9ca3af; font-size:0.95rem; margin-bottom:10px;">Incoming Post</div>
        <div id="ps-post" draggable="true" role="button" tabindex="0"
             style="display:flex; flex-direction:column; gap:10px; padding:14px; border-radius:12px; background:#1e1f2a; box-shadow:0 4px 12px rgba(0,0,0,0.5); cursor:grab; min-height:60px; max-width:450px;">
          <div id="ps-post-text" style="font-weight:600; font-size:1rem; color:#fff;">(Loading...)</div>
          <div id="ps-post-meta" style="font-size:0.85rem; color:#9ca3af;">&nbsp;</div>
        </div>
        <div style="margin-top:10px; font-size:0.9rem; color:#9ca3af;">Drag or use keyboard to sort this post into the correct category box.</div>
      </div>

      <!-- Category Boxes -->
      <div style="display:flex; flex-direction:column; gap:16px; flex:0 0 260px;">
        <div class="ps-drop" data-cat="Question" aria-label="Drop here for Question"
             style="min-height:80px; padding:14px; border-radius:12px; border:2px dashed #22c55e; background:#14532d; display:flex; flex-direction:column; justify-content:center; align-items:center; text-align:center;">
          <div style="font-weight:700; font-size:1rem; color:#d1fae5;">Question</div>
          <div style="font-size:0.85rem; color:#d1fae5;">Post asking for info or clarification</div>
        </div>

        <div class="ps-drop" data-cat="Opinion" aria-label="Drop here for Opinion"
             style="min-height:80px; padding:14px; border-radius:12px; border:2px dashed #f59e0b; background:#78350f; display:flex; flex-direction:column; justify-content:center; align-items:center; text-align:center;">
          <div style="font-weight:700; font-size:1rem; color:#fed7aa;">Opinion</div>
          <div style="font-size:0.85rem; color:#fed7aa;">Personal viewpoint or reaction</div>
        </div>

        <div class="ps-drop" data-cat="Announcement" aria-label="Drop here for Announcement"
             style="min-height:80px; padding:14px; border-radius:12px; border:2px dashed #6366f1; background:#1e1b4b; display:flex; flex-direction:column; justify-content:center; align-items:center; text-align:center;">
          <div style="font-weight:700; font-size:1rem; color:#c7d2fe;">Announcement</div>
          <div style="font-size:0.85rem; color:#c7d2fe;">News or site update post</div>
        </div>
      </div>
    </div>
  </section>
</div>

<script>
(function () {
  const POSTS = [
    { id:1,text:"Does anyone know when the site updates?",category:"Question"},
    { id:2,text:"I love the new features!",category:"Opinion"},
    { id:3,text:"Site will be down at 5 PM.",category:"Announcement"},
    { id:4,text:"Can someone explain microblogging?",category:"Question"},
    { id:5,text:"This layout is terrible.",category:"Opinion"},
    { id:6,text:"New moderation rules applied today.",category:"Announcement"},
    { id:7,text:"Who else uses microblogs for quick updates?",category:"Question"},
    { id:8,text:"I prefer concise posts to long threads.",category:"Opinion"},
    { id:9,text:"Maintenance scheduled for Sunday.",category:"Announcement"}
  ];

  const POSTS_PER_ROUND = 6;
  const SAVE_KEY = "postSorter_progress_dark";

  let queue=[], current=null, score=0, mistakes=0, index=0;

  const postTextEl = document.getElementById("ps-post-text");
  const postMetaEl = document.getElementById("ps-post-meta");
  const psPost = document.getElementById("ps-post");
  const scoreEl = document.getElementById("ps-score");
  const mistakesEl = document.getElementById("ps-mistakes");
  const restartBtn = document.getElementById("ps-restart");
  const dropZones = document.querySelectorAll(".ps-drop");

  function shuffle(arr){for(let i=arr.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));[arr[i],arr[j]]=[arr[j],arr[i]];}return arr;}

  function evaluateChoice(chosenCategory,currentPost){
    if(!currentPost||typeof chosenCategory!=="string"){return {correct:false,message:"Invalid input."};}
    const allowed=["Question","Opinion","Announcement"];
    let found=false;
    for(let i=0;i<allowed.length;i++){if(allowed[i]===chosenCategory){found=true;break;}}
    if(!found)return {correct:false,message:"Unknown category."};
    if(currentPost.category===chosenCategory)return {correct:true,message:"Correct!"};
    return {correct:false,message:"Incorrect."};
  }

  function updateUI(){scoreEl.textContent=score;mistakesEl.textContent=mistakes;}
  function renderCurrent(){if(!current){postTextEl.textContent="(No post)";postMetaEl.textContent="";psPost.setAttribute("aria-hidden","true");return;}postTextEl.textContent=current.text;postMetaEl.textContent="Drag me to the correct category";psPost.setAttribute("data-cat",current.category);psPost.setAttribute("aria-hidden","false");}

  function startRound(){queue=shuffle([...POSTS]).slice(0,POSTS_PER_ROUND);index=0;score=0;mistakes=0;current=null;updateUI();loadNext();saveProgress();}
  function loadNext(){if(index>=queue.length){finishRound();return;}current=queue[index];index++;renderCurrent();saveProgress();}
  function finishRound(){current=null;renderCurrent();saveProgress();setTimeout(()=>{alert("Round complete! Score: "+score+" | Mistakes: "+mistakes);},50);}
  function saveProgress(){try{localStorage.setItem(SAVE_KEY,JSON.stringify({queue,current,score,mistakes,index,timestamp:Date.now()}));}catch(e){}}
  function loadProgress(){try{const raw=localStorage.getItem(SAVE_KEY);if(!raw)return false;const p=JSON.parse(raw);if(!Array.isArray(p.queue)||typeof p.index!=="number")return false;queue=p.queue;current=p.current;score=p.score||0;mistakes=p.mistakes||0;index=p.index||0;updateUI();renderCurrent();return true;}catch(e){return false;}}

  function processUserChoice(chosenCategory){if(!current)return;const result=evaluateChoice(chosenCategory,current);if(result.correct){score+=1;flash("#22c55e");}else{mistakes+=1;flash("#ef4444");}updateUI();psPost.style.transform="translateY(-6px) scale(0.98)";psPost.style.opacity="0.6";setTimeout(()=>{psPost.style.transform="";psPost.style.opacity="1";loadNext();},240);}
  function flash(color){const el=document.getElementById("post-sorter-section");if(!el)return;const prev=el.style.boxShadow;el.style.boxShadow="0 0 0 4px "+color+"22";setTimeout(()=>{el.style.boxShadow=prev;},260);}

  psPost.addEventListener("dragstart",(e)=>{if(!current){e.preventDefault();return;}e.dataTransfer.setData("text/plain",JSON.stringify({id:current.id}));setTimeout(()=>{psPost.style.opacity="0.6";},0);});
  psPost.addEventListener("dragend",()=>{psPost.style.opacity="1";});

  let keyboardPicked=false;
  psPost.addEventListener("keydown",(e)=>{if(e.key===" "||e.key==="Enter"){e.preventDefault();keyboardPicked=!keyboardPicked;psPost.style.boxShadow=keyboardPicked?"0 8px 20px rgba(255,255,255,0.2)":"0 4px 10px rgba(0,0,0,0.5)";if(keyboardPicked)psPost.focus();}});

  dropZones.forEach(zone=>{zone.addEventListener("dragover",e=>{e.preventDefault();zone.style.opacity="0.9";});zone.addEventListener("dragleave",()=>{zone.style.opacity="1";});zone.addEventListener("drop",e=>{e.preventDefault();zone.style.opacity="1";if(!current)return;processUserChoice(zone.getAttribute("data-cat"));});zone.setAttribute("tabindex","0");zone.addEventListener("keydown",e=>{if((e.key==="Enter"||e.key===" ")&&keyboardPicked){e.preventDefault();keyboardPicked=false;psPost.style.boxShadow="0 4px 10px rgba(0,0,0,0.5)";processUserChoice(zone.getAttribute("data-cat"));}});});

  restartBtn.addEventListener("click",()=>{if(confirm("Restart the round? This will clear saved progress.")){localStorage.removeItem(SAVE_KEY);startRound();}});

  if(!loadProgress())startRound();
  updateUI();
  setInterval(saveProgress,2000);

  window.postSorter={startRound,loadProgress,saveProgress,evaluateChoice};
})();
</script>