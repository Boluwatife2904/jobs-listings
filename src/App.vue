<template>
  <div class="body-content" :class="{ 'low-space': filters.length > 0 }">
    <div class="filter-box" v-show="filters && filters.length > 0">
      <div class="filters">
        <filter-item
          v-for="filter in filters"
          :key="filter"
          :name="filter"
          @remove-filter="removeFilter"
        >
          {{ filter }}</filter-item
        >
      </div>
      <button @click="clearFilters">Clear</button>
    </div>
    <div class="jobs-container">
      <div v-for="job in filteredJobs" :key="job.id">
        <job-item :job="job" @set-filter="addFilter"></job-item>
      </div>
    </div>
  </div>
</template>

<script>
import JobItem from "./components/JobItem.vue";
import FilterItem from "./components/FilterItem.vue";

export default {
  name: "App",
  components: { JobItem, FilterItem },
  data() {
    return {
      filters: [],
      jobs: [
        {
          id: 1,
          company: "Photosnap",
          logo: require("./assets/images/photosnap.svg"),
          new: true,
          featured: true,
          position: "Senior Frontend Developer",
          role: "Frontend",
          level: "Senior",
          postedAt: "1d ago",
          contract: "Full Time",
          location: "USA Only",
          languages: ["HTML", "CSS", "JavaScript"],
          tools: [],
          tags: ["Frontend", "Senior", "HTML", "CSS", "JavaScript"],
        },
        {
          id: 2,
          company: "Manage",
          logo: require("./assets/images/manage.svg"),
          new: true,
          featured: true,
          position: "Fullstack Developer",
          role: "Fullstack",
          level: "Midweight",
          postedAt: "1d ago",
          contract: "Part Time",
          location: "Remote",
          languages: ["Python"],
          tools: ["React"],
          tags: ["Fullstack", "Midweight", "Python", "React"],
        },
        {
          id: 3,
          company: "Account",
          logo: require("./assets/images/account.svg"),
          new: true,
          featured: false,
          position: "Junior Frontend Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "2d ago",
          contract: "Part Time",
          location: "USA Only",
          languages: ["JavaScript"],
          tools: ["React", "Sass"],
          tags: ["Frontend", "Junior", "React", "Sass", "JavaScript"],
        },
        {
          id: 4,
          company: "MyHome",
          logo: require("./assets/images/myhome.svg"),
          new: false,
          featured: false,
          position: "Junior Frontend Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "5d ago",
          contract: "Contract",
          location: "USA Only",
          languages: ["CSS", "JavaScript"],
          tools: [],
          tags: ["Frontend", "Junior", "CSS", "JavaScript"],
        },
        {
          id: 5,
          company: "Loop Studios",
          logo: require("./assets/images/loop-studios.svg"),
          new: false,
          featured: false,
          position: "Software Engineer",
          role: "Fullstack",
          level: "Midweight",
          postedAt: "1w ago",
          contract: "Full Time",
          location: "Worldwide",
          languages: ["JavaScript"],
          tools: ["Ruby", "Sass"],
          tags: ["Fullstack", "Midweight", "JavaScript", "Sass", "Ruby"],
        },
        {
          id: 6,
          company: "FaceIt",
          logo: require("./assets/images/faceit.svg"),
          new: false,
          featured: false,
          position: "Junior Backend Developer",
          role: "Backend",
          level: "Junior",
          postedAt: "2w ago",
          contract: "Full Time",
          location: "UK Only",
          languages: ["Ruby"],
          tools: ["RoR"],
          tags: ["Backend", "Junior", "Ruby", "RoR"],
        },
        {
          id: 7,
          company: "Shortly",
          logo: require("./assets/images/shortly.svg"),
          new: false,
          featured: false,
          position: "Junior Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "2w ago",
          contract: "Full Time",
          location: "Worldwide",
          languages: ["HTML", "JavaScript"],
          tools: ["Sass"],
          tags: ["Frontend", "Junior", "HTML", "Sass", "JavaScript"],
        },
        {
          id: 8,
          company: "Insure",
          logo: require("./assets/images/insure.svg"),
          new: false,
          featured: false,
          position: "Junior Frontend Developer",
          role: "Frontend",
          level: "Junior",
          postedAt: "2w ago",
          contract: "Full Time",
          location: "USA Only",
          languages: ["JavaScript"],
          tools: ["Vue", "Sass"],
          tags: ["Frontend", "Junior", "Vue", "JavaScript", "Sass"],
        },
        {
          id: 9,
          company: "Eyecam Co.",
          logo: require("./assets/images/eyecam-co.svg"),
          new: false,
          featured: false,
          position: "Full Stack Engineer",
          role: "Fullstack",
          level: "Midweight",
          postedAt: "3w ago",
          contract: "Full Time",
          location: "Worldwide",
          languages: ["JavaScript", "Python"],
          tools: ["Django"],
          tags: ["Fullstack", "Midweight", "JavaScript", "Django", "Python"],
        },
        {
          id: 10,
          company: "The Air Filter Company",
          logo: require("./assets/images/the-air-filter-company.svg"),
          new: false,
          featured: false,
          position: "Front-end Dev",
          role: "Frontend",
          level: "Junior",
          postedAt: "1mo ago",
          contract: "Part Time",
          location: "Worldwide",
          languages: ["JavaScript"],
          tools: ["React", "Sass"],
          tags: ["Frontend", "Junior", "React", "Sass", "JavaScript"],
        },
      ],
    };
  },
  computed: {
    filteredJobs() {
      if (this.filters && this.filters.length > 0) {
        return this.jobs.filter((job) =>
          job.tags.some((item) => this.filters.indexOf(item) > -1)
        );
      }
      return this.jobs;
    },
  },
  methods: {
    addFilter(tag) {
      if (this.filters.indexOf(tag) > -1) {
        return;
      } else {
        this.filters.push(tag);
      }
    },
    removeFilter(tag) {
      this.filters = this.filters.filter((item) => item !== tag);
    },
    clearFilters() {
      this.filters = [];
    },
  },
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Spartan:wght@300;400;500;600;700&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: "Spartan", sans-serif;
  background: hsl(180, 52%, 96%);
  position: relative;
  z-index: 1;
}

body::after {
  position: absolute;
  content: "";
  top: 0;
  left: 0;
  height: 135px;
  background: url("./assets/images/bg-header-desktop.svg") hsl(180, 29%, 50%);
  width: 100%;
  background-position: center;
  background-size: cover;
  background-repeat: no-repeat;
  z-index: -1;

  @media screen and (max-width: 375px) {
    background: url("./assets/images/bg-header-mobile.svg") hsl(180, 29%, 50%);
  }
}

.body-content {
  padding-top: 190px;
  padding-bottom: 50px;
  max-width: 1024px;
  width: 90%;
  margin: auto;

  &.low-space {
    padding-top: 100px;
  }

  .filter-box {
    background: #ffffff;
    width: 100%;
    border-radius: 6px;
    padding: 15px 30px;
    margin-bottom: 30px;
    box-shadow: 2px 4px 26px 1px rgba(91, 164, 164, 0.2);
    display: flex;
    justify-content: space-between;
    align-items: center;

    button {
      outline: none;
      border: none;
      background: none;
      color: hsl(180, 29%, 50%);
      font: inherit;
      font-size: 14px;
      font-weight: 600;
      cursor: pointer;

      &:hover {
        text-decoration: underline;
      }
    }

    @media screen and (max-width: 576px) {
      margin-bottom: 50px;
    }
  }
}
</style>
