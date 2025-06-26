---
layout: default
title: Raid Assign
---

<div class="row justify-content-center">
  <div class="col-8 mb-5">
    <p class="text-center">Welcome to Bart's raid assignment project. This is a work in progress made for fun. I'm not a frontend developer, but I'm doing my best to make this look decent and functional. If you have feedback hit me up on discord.</p>
  </div>
  <div class="col-8 mb-5">
    <p class="text-center">If you landed on this page after expecting to see a raid, you probably clicked an old or invalid link. Ask your raid leader for a fresh link to your assignments.</p>
  </div>  
</div>
<div class="row">
  <div class="col-12 col-lg-6 d-flex justify-content-center align-items-center mb-5">
    <a href="create_raid" class="btn btn-lg btn-success">Create Raid</a>
  </div>
  <form method="get" action="raid" class="col-12 col-lg-6 d-flex justify-content-center align-items-center gap-2 mb-5">
    <input type="text" class="form-control" name="id" placeholder="Enter raid ID" required>
    <button type="submit" class="btn btn-primary text-nowrap">Go to Raid</button>
  </form>
</div>
