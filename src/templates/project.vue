<template>
  <Layout>
    <div class="project">
      <div class="container project-container">
        <div class="project-header">
          <h1 class="project-title">{{ $page.project.title }}</h1>
          <div class="project-meta">
            <div class="project-author">
              <span class="label">Categories</span>
              <span class="author-name">{{
                $page.project.categories.title
              }}</span>
            </div>
            <div class="project-date">
              <span class="label">year</span>
              <div>{{ $page.project.year }}</div>
            </div>
          </div>
        </div>
        <div class="project-content">
          {{ $page.project.content }}
        </div>
        <div>
          <g-image class="thumbnail" :src="`${GRIDSOME_API_URL + $page.project.image[0].url}`"></g-image>
        </div>
      </div>
    </div>
  </Layout>
</template>

<page-query>
  query ($id: ID!) {
    project: strapiProject (id: $id) {
      id
      title
      categories {
        title
      }
      year
      content
      image {
        url(width: 500, height: 200, quality: 90)
      }
    }
  }
</page-query>

<script>
  export default {
    name: "ProjectTemplate",
  };
</script>

<style>
  * {
    box-sizing: border-box;
  }
  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
  }
  .project-container {
    max-width: 840px;
  }
  .project-header {
    padding: 2rem 0 4rem;
  }
  .project-title {
    font-size: 4rem;
    margin: 0 0 4rem;
    padding: 0;
  }
  .project-meta {
    display: flex;
    flex-wrap: wrap;
    font-size: 0.8rem;
  }
  .project-author {
    margin-right: 4rem;
  }
  .project-date {
    margin-right: 4rem;
  }
  .project-time {
    margin: 0;
  }
  .label {
    display: block;
    font-weight: 700;
    margin-bottom: 0.5rem;
  }
  .thumbnail {
    max-width: 100%;
    height: 560px;
    object-fit: cover;
    transition: all .15s ease;
    box-shadow: 0 0 40px -20px rgba(0 0 0 0.25);
  }
</style>
