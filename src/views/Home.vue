<template>
  <div class="home">
    <navbar></navbar>
    <div class="profile-intro-section flex justify-center">
      <div class="">
        <div class="profile--intro-text">It's me, Korarit P.</div>
        <div class="profile--decription-text">
          Currently a 4-th year Computer Engineering student at <br class="newline"/>King
          Mongkut's University of Technology Thonburi <br />
        </div>
        <div class="profile--contact ">
          <div class="profile--resume-btn">
            <a href="Korarit_Resume.pdf" download="korarit_resume"
              >Get My Resume</a
            >
          </div>
          <div class="profile--go-to-to-do-btn" @click="gotoToDoPage">
            To-Do Page
          </div>
        </div>
      </div>
      <div>
        <div class="profile--img-section ml-8">
          <img src="../assets/profile.jpg" class="profile--img hidden md:flex" />
        </div>
      </div>
    </div>
    <div class="senior-project-section">
      <div class="senior--topic-text">
        <Icon
          icon="heroicons-outline:arrow-circle-right"
          class="arrow-circle-right--icon"
        />My Senior Project
      </div>
      <div class="senior--logo-section hidden md:flex">
        <img
          src="../assets/expand_configchain_logo.png"
          class="logo-configchain--img"
        />
      </div>
      <div class="senior--decription-text">
        <span>
          <span class="text--bold">ConfigChain </span>
          is web application for network configuration management with
          blockchain technology. The main objective of this project is creating
          network management system and apply blockchain technology to store
          some sensitive data such as configuration history. <br />
        </span>
        <div class="text--right mt-8 pb-5">
          This project is cooperates with
          <span class="text--highlight"
            >National Telecom Public Company Limited</span
          >.
        </div>
      </div>
    </div>
    <div class="skill-section">
      <div class="skill--topic">My Technical Skills</div>
      <div class="skill--topic-text">Website Technologies</div>
      <div class="skill--card">
        <skill-card
          v-for="(skill, index) in webSkills"
          :key="index"
          :icon="skill.icon"
          :text="skill.text"
        ></skill-card>
      </div>
      <div class="skill--topic-text mt-5">Programming Languages</div>
      <div class="skill--card">
        <skill-card
          v-for="(lang, index) in programmingLanguages"
          :key="index"
          :icon="lang.icon"
          :text="lang.text"
        ></skill-card>
      </div>
      <div class="skill--topic-text mt-5">Utility Tools</div>
      <div class="skill--card">
        <skill-card
          v-for="(tool, index) in tools"
          :key="index"
          :icon="tool.icon"
          :text="tool.text"
        ></skill-card>
      </div>
    </div>
    <div class="courses-section">
      <div class="courses--topic-text">
        <Icon
          icon="heroicons-outline:arrow-circle-right"
          class="arrow-circle-right--icon"
        />Course
      </div>
      <div class="course--card">
        <course-card
          v-for="(course, index) in courses"
          :key="index"
          :text="course"
        ></course-card>
      </div>
    </div>
    <div class="footer-section">
      <div class="footer--text ml-5">Build by me, Korarit using Vue.js</div>
      <div class="footer--text mr-5">
        <Icon
          icon="flat-color-icons:business-contact"
          class="business-contact--icon"
        />Contact Me : korarit.pr@gmail.com | (+66)96 996 9549
      </div>
    </div>
  </div>
</template>

<script>
import { Icon } from "@iconify/vue2"
import navbar from "../components/Navbar.vue"
import SkillCard from "../components/SkillCard.vue"
import CourseCard from "../components/CourseCard.vue"
export default {
  name: "Home",
  components: {
    navbar,
    Icon,
    SkillCard,
    CourseCard,
  },
  data() {
    return {
      webSkills: [
        { icon: "vscode-icons:file-type-html", text: "HTML5" },
        { icon: "vscode-icons:file-type-css", text: "CSS" },
        { icon: "logos:javascript", text: "JavaScript" },
        { icon: "logos:vue", text: "Vue.js" },
      ],
      programmingLanguages: [
        { icon: "noto-v1:letter-c", text: "C" },
        { icon: "vscode-icons:file-type-python", text: "Python" },
        { icon: "logos:java", text: "Java" },
        { icon: "vscode-icons:file-type-go", text: "Go" },
      ],
      tools: [
        { icon: "codicon:github", text: "Git" },
        { icon: "gg:figma", text: "Figma" },
        { icon: "fa-brands:trello", text: "Trello" },
        { icon: "simple-icons:jirasoftware", text: "Jira" },
      ],
      courses: [
        "Software Engineering",
        "Human-Computer Interaction",
        "Commercializing Project",
        "Blockchain Technology",
        "Modern Programming Language",
        "Data Model",
      ],
    }
  },
  methods: {
    gotoToDoPage() {
      this.$router.push("/to-do-page")
    },
  },
}
</script>

<style lang="scss" scoped>
.home {
  background-color: #f1f4f8;
}

.newline {
  display: none;
}

.profile-intro-section {
  background-color: #3778c2;
  box-shadow: inset 0 0 15px rgba($color: #3e4c59, $alpha: 0.4);
  padding-top: 2rem;
  padding-bottom: 3rem;
}

.profile--intro-text {
  display: flex;
  color: white;
  padding-top: 6rem;
  padding-left: 3rem;
  font-size: 2rem;
  font-weight: 600;
}

.profile--decription-text {
  display: flex;
  color: #f0ffff;
  padding-left: 3rem;
  line-height: 2.5rem;
  font-size: 0.85rem;
}

.profile--resume-btn {
  background-color: white;
  color: #3e4c59;
  border-style: solid;
  border-color: white;
  border-width: 2px;
  border-radius: 6px;
  padding: 0.75rem 1.5rem;
  margin-right: 2rem;
  font-weight: 500;
  &:hover {
    cursor: pointer;
    background: whitesmoke;
    color: #3e4c59;
  }
}

.profile--go-to-to-do-btn {
  border-style: solid;
  border-color: white;
  border-width: 2px;
  border-radius: 6px;
  padding: 0.75rem 1.5rem;
  margin-right: 2.5rem;
  font-weight: 500;
  &:hover {
    cursor: pointer;
    background: whitesmoke;
    color: #3e4c59;
  }
}

.profile--contact {
  display: flex;
  font-size: 0.89rem;
  padding-left: 3rem;
  color: white;
  margin-top: 1rem;
}

.profile--img-section {
  display: flex;
  justify-content: left;
  margin-top: 70px;
}

.profile--img {
  border-style: solid;
  border-color: white;
  border-width: 0.4rem;
  border-radius: 50%;
  width: 280px;
  height: 280px;
}

.senior-project-section,
.courses-section {
  background-color: #f1f4f8;
  padding: 0.75rem 2rem;
}

.arrow-circle-right--icon {
  display: inline;
  margin-right: 8px;
  font-size: 1.75rem;
  font-weight: 600;
}

.senior--topic-text,
.courses--topic-text {
  color: #568be4;
  padding-top: 2rem;
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.senior--logo-section {
  display: flex;
  justify-content: center;
}

.logo-configchain--img {
  margin-top: 1rem;
  display: flex;
  height: 90px;
  width: 376px;
}

.senior--decription-text {
  color: #3e4c59;
  margin-top: 3rem;
  font-size: 0.85rem;
  line-height: 2.25rem;
}

.text--bold {
  font-weight: 600;
}

.text--highlight {
  color: #568be4;
}

.text--right {
  text-align: right;
}

.skill-section {
  box-shadow: inset 0 0 10px rgba($color: #3e4c59, $alpha: 0.09);
  background-color: rgba($color: #3778c2, $alpha: 0.05);
  padding-bottom: 2rem;
}

.skill--topic {
  display: flex;
  justify-content: center;
  padding-top: 2rem;
  color: #568be4;
  font-size: 2rem;
  font-weight: 600;
}

.skill--topic-text {
  padding-top: 2rem;
  display: flex;
  justify-content: center;
  text-align: left;
  color: #3e4c59;
  font-size: 1.25rem;
  font-weight: 500;
}

.skill--card {
  display: flex;
  justify-content: center;
  margin-top: 2rem;
}

.course--card {
  display: flexblock;
  margin-top: 2rem;
}

.footer-section {
  display: flex;
  justify-content: space-between;
  padding: 0.75rem 0;
  background-color: #3e4c59;
}

.footer--text {
  color: white;
  display: flex;
  justify-content: center;
  font-size: 0.4rem;
  font-weight: 400;
}

.business-contact--icon {
  display: none;
}

// Small devices (landscape phones, 576px and up)
@media screen and (min-width: 576px) {
}

// Medium devices (tablets, 768px and up)
@media screen and (min-width: 768px) {
  .newline {
  display: block;
}
  .profile--intro-text {

  font-size: 3rem;

}
  .logo-configchain--img {
  height: 120px;
  width: 476px;
}
.senior--decription-text {
  font-size: 1.125rem;
}
}

// Large devices (desktops, 992px and up)
@media screen and (min-width: 992px) {
  .senior-project-section,
  .courses-section {
    background-color: #f1f4f8;
    padding: 0.75rem 10rem;
  }
  .footer--text {
    font-size: 0.9rem;
  }
  .business-contact--icon {
    display: flex;
    font-size: 1.45rem;
}
  .profile--contact {
  padding-top: 1rem;
  padding-left: 3rem;
  margin-top: 1rem;
}
}

// Extra large devices (large desktops, 1200px and up)
@media screen and (min-width: 1200px) {
  .senior-project-section,
  .courses-section {
    background-color: #f1f4f8;
    padding: 0.75rem 18rem;
  }
  .profile-intro-section {
    padding: 0 10rem;
    padding-top: 2rem;
    padding-bottom: 5rem;
  }
  .profile-intro-text {
    font-size: 4.75rem;
  }
  .profile--decription-text{
    font-size: 1.125rem;
  }
}

@media screen and (min-width: 1524px) {
  .senior-project-section,
  .courses-section {
    background-color: #f1f4f8;
    padding: 0.75rem 28rem;
  }
  .profile-intro-section {
    padding: 0 16rem;
    padding-top: 2rem;
    padding-bottom: 5rem;
  }
}
</style>
