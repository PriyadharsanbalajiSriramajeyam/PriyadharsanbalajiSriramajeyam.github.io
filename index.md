---
layout: default
title: Welcome
---

<div class="intro-page">
  <div class="intro-content">
    <div class="profile-section">
      <img src="/img/profile_pic.jpg" alt="Profile Picture" class="profile-image">
      <div class="profile-text">
        <p>I am working as machine learning engineer at Immerso.ai. My work over here is to do foundational models for text to image and video generation at scale for movie generation.</p>

        <p>I have spent my MS at IIT Madras working under kaushik mitra. I have been working on 3d and 2d in the fields of image generation and restoration.</p>

        <p>I hate to sociualize but I do put my efforts to make new friends who are like minded, if you are interested in computer vision, computational imaging, math, cats and music. A cheat way is to share insta reels which are funny.</p>
      </div>
    </div>

    <div class="intro-links">
      <h2>Explore More</h2>
      <div class="link-buttons">
        <a href="/research" class="intro-link-btn">Research</a>
        <a href="/resume" class="intro-link-btn">Resume</a>
        <a href="/archive" class="intro-link-btn">Blog Posts</a>
        <a href="/about_me" class="intro-link-btn">About Me</a>
      </div>
    </div>

    <div class="intro-social">
      <h2>Connect</h2>
      <div class="social-links">
        {% if site.github_username %}
          <a href="https://github.com/{{ site.github_username }}" target="_blank" rel="noopener">GitHub</a>
        {% endif %}
        {% if site.linkedin_username %}
          <a href="https://linkedin.com/in/{{ site.linkedin_username }}" target="_blank" rel="noopener">LinkedIn</a>
        {% endif %}
        {% if site.twitter_username %}
          <a href="https://twitter.com/{{ site.twitter_username }}" target="_blank" rel="noopener">Twitter</a>
        {% endif %}
      </div>
    </div>
  </div>
</div>

<style>
.intro-page {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

.intro-content {
  line-height: 1.7;
}

.profile-section {
  display: flex;
  gap: 2rem;
  align-items: flex-start;
  margin-bottom: 3rem;
}

.profile-image {
  width: 250px;
  height: auto;
  border-radius: 8px;
  flex-shrink: 0;
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

.profile-text {
  flex: 1;
  font-size: 1rem;
  color: #444;
}

.profile-text p {
  margin-bottom: 1.2rem;
}

.intro-links, .intro-social {
  margin-top: 3rem;
  text-align: center;
}

.intro-links h2, .intro-social h2 {
  margin-bottom: 1.5rem;
  color: #333;
  font-size: 1.4rem;
}

.link-buttons {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
}

.intro-link-btn {
  display: inline-block;
  padding: 0.6rem 1.2rem;
  background: #555;
  color: white;
  text-decoration: none;
  border-radius: 4px;
  transition: background 0.2s ease;
  font-weight: normal;
}

.intro-link-btn:hover {
  background: #333;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
}

.social-links a {
  color: #555;
  text-decoration: none;
  font-size: 1rem;
  transition: color 0.2s ease;
}

.social-links a:hover {
  color: #333;
  text-decoration: underline;
}

@media (max-width: 768px) {
  .profile-section {
    flex-direction: column;
    align-items: center;
  }
  
  .profile-image {
    width: 200px;
  }
  
  .link-buttons {
    flex-direction: column;
    align-items: center;
  }
  
  .intro-link-btn {
    width: 180px;
  }
}
</style>
