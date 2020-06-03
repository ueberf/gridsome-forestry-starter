<template>
  <Layout>
    <div class="container">
      <Hero />
      <div class="" v-html= "settings.featured_posts">
      </div>

      <ProjectsGrid :projects="$page.projects.edges" />
    </div>
    <LatestJournals :journals="$page.journals.edges" />
  </Layout>
</template>

<page-query>
query Posts {
	projects: allProjectPost {
    edges {
      node {
        id
        date (format: "YYYY")
        title
        categories
        thumbnail (quality: 90)
        path
      }
    }
  },
  journals: allJournalPost (perPage: 4) {
    edges {
      node {
        id
        path
        title
      }
    }
  }
}
</page-query>

<script>
import Hero from "@/components/Hero"
import ProjectsGrid from "@/components/ProjectsGrid"
import LatestJournals from "@/components/LatestJournals"
import settings from "../../data/theme.json"

export default {
  components: {
    Hero,
    ProjectsGrid,
    LatestJournals
  },
  data(){
    return{
      settings
    }
  }
}
</script>
