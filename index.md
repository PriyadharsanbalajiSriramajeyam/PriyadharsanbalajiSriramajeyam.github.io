---
layout: default
title: Welcome
---

<div class="intro-page">
  <div class="intro-header">
    <h1 class="intro-name">{{ site.data.resume.header.name }}</h1>
    <p class="intro-title">{{ site.data.resume.header.suffix }} • {{ site.data.resume.header.current_title }}</p>
  </div>

  <div class="intro-content">
    <div class="intro-text">
      <p class="intro-description">{{ site.data.resume.header.intro }}</p>
    </div>

    <div class="intro-highlights">
      <div class="highlight-section">
        <h2>📍 Current Role</h2>
        {% assign current_exp = site.data.experience[0] %}
        {% assign current_pos = current_exp.positions[0] %}
        <p><strong>{{ current_pos.title }}</strong> at {{ current_exp.company }}</p>
        <p class="highlight-summary">{{ current_pos.summary }}</p>
      </div>

      <div class="highlight-section">
        <h2>🎓 Education</h2>
        {% assign latest_edu = site.data.education[0] %}
        <p><strong>{{ latest_edu.degree }}</strong></p>
        <p>{{ latest_edu.uni }} • {{ latest_edu.year }}</p>
        <p class="highlight-summary">{{ latest_edu.summary }}</p>
      </div>

      <div class="highlight-section">
        <h2>💼 Key Skills</h2>
        <ul class="skills-list">
          {% for skill in site.data.skills limit:3 %}
            <li>
              <strong>{{ skill.skill }}:</strong>
              {% if skill.description %}
                {{ skill.description | strip_html | truncatewords: 20 }}
              {% elsif skill.list %}
                {{ skill.list | join: " • " }}
              {% endif %}
            </li>
          {% endfor %}
        </ul>
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
  max-width: 900px;
  margin: 0 auto;
  padding: 2rem 1rem;
}

.intro-header {
  text-align: center;
  margin-bottom: 3rem;
  padding-bottom: 2rem;
  border-bottom: 2px solid #e8e8e8;
}

.intro-name {
  font-size: 2.5rem;
  margin-bottom: 0.5rem;
  color: #333;
}

.intro-title {
  font-size: 1.2rem;
  color: #666;
  margin: 0;
}

.intro-content {
  line-height: 1.8;
}

.intro-text {
  margin-bottom: 3rem;
}

.intro-description {
  font-size: 1.1rem;
  color: #444;
  text-align: justify;
}

.intro-highlights {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.highlight-section {
  background: #f8f9fa;
  padding: 1.5rem;
  border-radius: 8px;
  border-left: 4px solid #007acc;
}

.highlight-section h2 {
  font-size: 1.3rem;
  margin-top: 0;
  margin-bottom: 1rem;
  color: #333;
}

.highlight-section p {
  margin: 0.5rem 0;
  color: #555;
}

.highlight-summary {
  font-size: 0.95rem;
  color: #666;
  font-style: italic;
}

.skills-list {
  list-style: none;
  padding-left: 0;
}

.skills-list li {
  margin-bottom: 0.8rem;
  color: #555;
}

.intro-links, .intro-social {
  margin-top: 3rem;
  text-align: center;
}

.intro-links h2, .intro-social h2 {
  margin-bottom: 1.5rem;
  color: #333;
}

.link-buttons {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 1rem;
}

.intro-link-btn {
  display: inline-block;
  padding: 0.75rem 1.5rem;
  background: #007acc;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  transition: background 0.3s ease;
  font-weight: 500;
}

.intro-link-btn:hover {
  background: #005a9e;
}

.social-links {
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
}

.social-links a {
  color: #007acc;
  text-decoration: none;
  font-size: 1.1rem;
  transition: color 0.3s ease;
}

.social-links a:hover {
  color: #005a9e;
  text-decoration: underline;
}

@media (max-width: 768px) {
  .intro-name {
    font-size: 2rem;
  }
  
  .intro-highlights {
    grid-template-columns: 1fr;
  }
  
  .link-buttons {
    flex-direction: column;
    align-items: center;
  }
  
  .intro-link-btn {
    width: 200px;
  }
}
</style>
