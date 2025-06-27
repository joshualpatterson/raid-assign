---
layout: default
page_type: about
title: About
---

<div class="container">
  <div class="card mb-5">
    <div class="card-body">
      <h2>What is this?</h2>
      <p>This simple site was built to handle World of Warcraft Classic raid assignments. In more organized raid groups I've been a part of there were often spreadsheets with lots of useful, albeit cluttered, information for various players to be familiar with. Things like tank targets, healing assignments, buff groups, etc. In theory, having all of this information established beforehand allows the raid to run smoothly while reducing the amount of on-the-fly instructions and call-outs.</p>
      <p>The issue I've often encountered is the analysis paralysis most humans face when trying to find their name amongst a sea of information not relevant to them. I have ADHD and could never remember my assignments between encounters. Thus, I would often alt-tab between these spreadsheets and the game in order to keep track, and finding my assignment for that particular encounter was often a lot of extra effort.</p>
      <p>This site has two objectives: (1) create a tool for raid leaders to setup assignments quickly and easily and (2) create a web interface for players to be able to more easily view their own assignments.</p>
    </div>
  </div>
  <div class="card mb-5">
    <div class="card-body">
      <h2>How does it work?</h2>
      <p>This is a static site hosted with GitHub pages, a free tool but one that is limited in backend functionality. This means all of the processing and logic is client-based (done by your browser) when it is used.</p>
      <p>In order for raids to be persistent and viewable by more than just you in your own browser, we leverage another free tool hosted by GitHub called Gists. These are publicly available code files you can create and save fairly easily with the intention of sharing code snippets and simple text files. Gists can be used to store a data file type called json, which is more than enough to capture a raid's worth of assignment data.</p>
      <p>When you load a raid, your browser is fetching the json file associated with that raid ID and using some basic javascript to populate the page with it. And that's it!</p>
    </div>
  </div>
</div>
