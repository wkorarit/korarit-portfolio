<template>
  <div class="container--to-do-page">
    <div class="sorry--section">
      <div class="sad-icon--container">
        <Icon icon="emojione:sad-but-relieved-face" class="sad--icon" />
      </div>
      <div class="text-center text-2xl mt-5">Sorry, This Page is only support on desktop screen size.</div>
      <div class="text-center text-xl">please use others devices which have larger screen.</div>
      <div class="sorry-page-back-to-home-btn mt-5" @click="linkToHome">
            Go Back to Home Page
      </div>
    </div>
    <div class="to-do-page">
      <navbar></navbar>
      <div class="to-do-page--intro-section">
        <div class="intro-icon">
          <Icon
            icon="fluent:task-list-square-rtl-24-filled"
            class="task-list--icon"
          />
        </div>
        <div class="intro-text mt-1">
          This page is an example of function which create from HTML5, CSS,
          JavaScript and Vue.js
        </div>
        <div class="intro-description mt-3">
          This function is using your local storage as a database. In case that
          you want to clear data in your local storage, you can click at "Clear
          Local Storage" button below.
        </div>
        <div class="intro-btn mt-5">
          <div class="back-to-home-btn" @click="linkToHome">
            Go Back to Home Page
          </div>
          <div class="clear-local-btn" @click="clearDataStorage">
            Clear Local Storage
          </div>
        </div>
      </div>
      <div class="to-do-page--card-box">
        <div class="to-do-page--add-card">
          <div class="to-do-page--add-card-topic">Add New Task</div>
          <div class="to-do-page--add-card-input-topic">
            Topic
            <input type="text" class="input-topic" v-model="newTask.topic" />
          </div>
          <div class="to-do-page--add-card-input-date mt-3">
            Date
            <flat-pickr
              v-model="newTask.date"
              class="input-date"
              :config="config"
            ></flat-pickr>
          </div>
          <div class="to-do-page--add-card-input-description mt-4">
            Description
            <textarea
              class="input-description"
              v-model="newTask.description"
            ></textarea>
          </div>
          <div class="to-do-page--add-card-input-urgent mt-3 ml-1">
            <base-checkbox v-model="newTask.isUrgent"></base-checkbox>
            <div class="urgent-text">This task is URGENT!</div>
          </div>
          <div class="to-do-page--add-card-add-btn-containter mt-5">
            <div class="add-btn" @click="addNewTask()">Add</div>
          </div>
        </div>
        <div class="to-do-page--show-card">
          <div class="grid grid-cols-7 sun-color">
            <div class="sun-task">
              <div class="day-flex-center">Sunday</div>
              <div
                class="task-card"
                v-for="(task, index) in sunTask"
                :key="index"
                :class="{ 'finish-card': task.isClear }"
              >
                <div class="task-card--topic">
                  <div class="card-topic">
                    <span>{{ task.topic }}</span
                    ><Icon
                      icon="fxemoji:fire"
                      class="fire--icon"
                      v-show="task.isUrgent"
                    />
                  </div>
                  <div class="card-btn-delete" @click="deleteTask(task)">
                    <Icon icon="ion:trash-bin" class="trash--icon" />
                  </div>
                </div>
                <div class="task-card--description mt-2">
                  <span>{{ task.description }}</span>
                </div>
                <div class="task-card--footer mt-3">
                  <div class="finish-checkbox">
                    <finish-task-checkbox
                      v-model="task.isClear"
                    ></finish-task-checkbox>
                    <div class="ml-2">Finish</div>
                  </div>
                  <span>{{ task.date }}</span>
                </div>
              </div>
            </div>
            <div class="mon-task">
              <div class="day-flex-center">Monday</div>
              <div
                class="task-card"
                v-for="(task, index) in monTask"
                :key="index"
                :class="{ 'finish-card': task.isClear }"
              >
                <div class="task-card--topic">
                  <div class="card-topic">
                    <span>{{ task.topic }}</span
                    ><Icon
                      icon="fxemoji:fire"
                      class="fire--icon"
                      v-show="task.isUrgent"
                    />
                  </div>
                  <div class="card-btn-delete" @click="deleteTask(task)">
                    <Icon icon="ion:trash-bin" class="trash--icon" />
                  </div>
                </div>
                <div class="task-card--description mt-2">
                  <span>{{ task.description }}</span>
                </div>
                <div class="task-card--footer mt-3">
                  <div class="finish-checkbox">
                    <finish-task-checkbox
                      v-model="task.isClear"
                    ></finish-task-checkbox>
                    <div class="ml-2">Finish</div>
                  </div>
                  <span>{{ task.date }}</span>
                </div>
              </div>
            </div>
            <div class="tue-task">
              <div class="day-flex-center">Tuesday</div>
              <div
                class="task-card"
                v-for="(task, index) in tueTask"
                :key="index"
                :class="{ 'finish-card': task.isClear }"
              >
                <div class="task-card--topic">
                  <div class="card-topic">
                    <span>{{ task.topic }}</span
                    ><Icon
                      icon="fxemoji:fire"
                      class="fire--icon"
                      v-show="task.isUrgent"
                    />
                  </div>
                  <div class="card-btn-delete" @click="deleteTask(task)">
                    <Icon icon="ion:trash-bin" class="trash--icon" />
                  </div>
                </div>
                <div class="task-card--description mt-2">
                  <span>{{ task.description }}</span>
                </div>
                <div class="task-card--footer mt-3">
                  <div class="finish-checkbox">
                    <finish-task-checkbox
                      v-model="task.isClear"
                    ></finish-task-checkbox>
                    <div class="ml-2">Finish</div>
                  </div>
                  <span>{{ task.date }}</span>
                </div>
              </div>
            </div>
            <div class="wed-task">
              <div class="day-flex-center">Wednesday</div>
              <div
                class="task-card"
                v-for="(task, index) in wedTask"
                :key="index"
                :class="{ 'finish-card': task.isClear }"
              >
                <div class="task-card--topic">
                  <div class="card-topic">
                    <span>{{ task.topic }}</span
                    ><Icon
                      icon="fxemoji:fire"
                      class="fire--icon"
                      v-show="task.isUrgent"
                    />
                  </div>
                  <div class="card-btn-delete" @click="deleteTask(task)">
                    <Icon icon="ion:trash-bin" class="trash--icon" />
                  </div>
                </div>
                <div class="task-card--description mt-2">
                  <span>{{ task.description }}</span>
                </div>
                <div class="task-card--footer mt-3">
                  <div class="finish-checkbox">
                    <finish-task-checkbox
                      v-model="task.isClear"
                    ></finish-task-checkbox>
                    <div class="ml-2">Finish</div>
                  </div>
                  <span>{{ task.date }}</span>
                </div>
              </div>
            </div>
            <div class="thu-task">
              <div class="day-flex-center">Thursday</div>
              <div
                class="task-card"
                v-for="(task, index) in thuTask"
                :key="index"
                :class="{ 'finish-card': task.isClear }"
              >
                <div class="task-card--topic">
                  <div class="card-topic">
                    <span>{{ task.topic }}</span
                    ><Icon
                      icon="fxemoji:fire"
                      class="fire--icon"
                      v-show="task.isUrgent"
                    />
                  </div>
                  <div class="card-btn-delete" @click="deleteTask(task)">
                    <Icon icon="ion:trash-bin" class="trash--icon" />
                  </div>
                </div>
                <div class="task-card--description mt-2">
                  <span>{{ task.description }}</span>
                </div>
                <div class="task-card--footer mt-3">
                  <div class="finish-checkbox">
                    <finish-task-checkbox
                      v-model="task.isClear"
                    ></finish-task-checkbox>
                    <div class="ml-2">Finish</div>
                  </div>
                  <span>{{ task.date }}</span>
                </div>
              </div>
            </div>
            <div class="fri-task">
              <div class="day-flex-center">Friday</div>
              <div
                class="task-card"
                v-for="(task, index) in friTask"
                :key="index"
                :class="{ 'finish-card': task.isClear }"
              >
                <div class="task-card--topic">
                  <div class="card-topic">
                    <span>{{ task.topic }}</span
                    ><Icon
                      icon="fxemoji:fire"
                      class="fire--icon"
                      v-show="task.isUrgent"
                    />
                  </div>
                  <div class="card-btn-delete" @click="deleteTask(task)">
                    <Icon icon="ion:trash-bin" class="trash--icon" />
                  </div>
                </div>
                <div class="task-card--description mt-2">
                  <span>{{ task.description }}</span>
                </div>
                <div class="task-card--footer mt-3">
                  <div class="finish-checkbox">
                    <finish-task-checkbox
                      v-model="task.isClear"
                    ></finish-task-checkbox>
                    <div class="ml-2">Finish</div>
                  </div>
                  <span>{{ task.date }}</span>
                </div>
              </div>
            </div>
            <div class="sat-task">
              <div class="day-flex-center">Saturday</div>
              <div
                class="task-card"
                v-for="(task, index) in satTask"
                :key="index"
                :class="{ 'finish-card': task.isClear }"
              >
                <div class="task-card--topic">
                  <div class="card-topic">
                    <span>{{ task.topic }}</span
                    ><Icon
                      icon="fxemoji:fire"
                      class="fire--icon"
                      v-show="task.isUrgent"
                    />
                  </div>
                  <div class="card-btn-delete" @click="deleteTask(task)">
                    <Icon icon="ion:trash-bin" class="trash--icon" />
                  </div>
                </div>
                <div class="task-card--description mt-2">
                  <span>{{ task.description }}</span>
                </div>
                <div class="task-card--footer mt-3">
                  <div class="finish-checkbox">
                    <finish-task-checkbox
                      v-model="task.isClear"
                    ></finish-task-checkbox>
                    <div class="ml-2">Finish</div>
                  </div>
                  <span>{{ task.date }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Icon } from "@iconify/vue2"
import Navbar from "../components/Navbar.vue"
import flatPickr from "vue-flatpickr-component"
import "flatpickr/dist/flatpickr.css"
import BaseCheckbox from "../components/BaseCheckbox.vue"
import FinishTaskCheckbox from "../components/FinishTaskCheckbox.vue"
export default {
  components: { Icon, Navbar, flatPickr, BaseCheckbox, FinishTaskCheckbox },
  name: "ToDoPage",
  data() {
    return {
      tasknumber: 1,
      config: {
        altFormat: "D M j, Y",
        altInput: true,
        dateFormat: "D Y-m-d",
      },
      newTask: {
        tasknum: 0,
        topic: "",
        description: "",
        date: null,
        isUrgent: false,
        isClear: false,
      },
      sunTask: [],
      monTask: [],
      tueTask: [],
      wedTask: [],
      thuTask: [],
      friTask: [],
      satTask: [],
    }
  },
  mounted() {
    this.fetchData()
  },
  methods: {
    addNewTask() {
      console.log(this.newTask)
      if (this.newTask.date === null) {
        return
      }
      if (this.newTask.date.includes("Sun")) {
        this.sunTask.push(this.newTask)
        this.sunTask.sort(this.compare)
      } else if (this.newTask.date.includes("Mon")) {
        this.monTask.push(this.newTask)
        this.monTask.sort(this.compare)
      } else if (this.newTask.date.includes("Tue")) {
        this.tueTask.push(this.newTask)
        this.tueTask.sort(this.compare)
      } else if (this.newTask.date.includes("Wed")) {
        this.wedTask.push(this.newTask)
        this.wedTask.sort(this.compare)
      } else if (this.newTask.date.includes("Thu")) {
        this.thuTask.push(this.newTask)
        this.thuTask.sort(this.compare)
      } else if (this.newTask.date.includes("Fri")) {
        this.friTask.push(this.newTask)
        this.friTask.sort(this.compare)
      } else if (this.newTask.date.includes("Sat")) {
        this.satTask.push(this.newTask)
        this.satTask.sort(this.compare)
      }
      this.saveOnLocal()
      this.tasknumber = this.tasknumber + 1
      this.newTask = {
        tasknum: this.tasknumber,
        topic: "",
        description: "",
        date: null,
        isUrgent: false,
        isClear: false,
      }
    },
    deleteTask(task) {
      if (task.date.includes("Sun")) {
        const index = this.sunTask.findIndex((object) => {
          return object.tasknum === task.tasknum
        })
        this.sunTask.splice(index, 1)
        localStorage.setItem("sunTask", JSON.stringify(this.sunTask))
      } else if (task.date.includes("Mon")) {
        const index = this.monTask.findIndex((object) => {
          return object.tasknum === task.tasknum
        })
        this.monTask.splice(index, 1)
        localStorage.setItem("monTask", JSON.stringify(this.monTask))
      } else if (task.date.includes("Tue")) {
        const index = this.tueTask.findIndex((object) => {
          return object.tasknum === task.tasknum
        })
        this.tueTask.splice(index, 1)
        localStorage.setItem("tueTask", JSON.stringify(this.tueTask))
      } else if (task.date.includes("Wed")) {
        const index = this.wedTask.findIndex((object) => {
          return object.tasknum === task.tasknum
        })
        this.wedTask.splice(index, 1)
        localStorage.setItem("wedTask", JSON.stringify(this.wedTask))
      } else if (task.date.includes("Thu")) {
        const index = this.thuTask.findIndex((object) => {
          return object.tasknum === task.tasknum
        })
        this.thuTask.splice(index, 1)
        localStorage.setItem("thuTask", JSON.stringify(this.thuTask))
      } else if (task.date.includes("Fri")) {
        const index = this.friTask.findIndex((object) => {
          return object.tasknum === task.tasknum
        })
        this.friTask.splice(index, 1)
        localStorage.setItem("friTask", JSON.stringify(this.friTask))
      } else if (task.date.includes("Sat")) {
        const index = this.satTask.findIndex((object) => {
          return object.tasknum === task.tasknum
        })
        this.satTask.splice(index, 1)
        localStorage.setItem("satTask", JSON.stringify(this.satTask))
      }
    },
    saveOnLocal() {
      localStorage.setItem("taskNumber", JSON.stringify(this.tasknumber))
      localStorage.setItem("sunTask", JSON.stringify(this.sunTask))
      localStorage.setItem("monTask", JSON.stringify(this.monTask))
      localStorage.setItem("tueTask", JSON.stringify(this.tueTask))
      localStorage.setItem("wedTask", JSON.stringify(this.wedTask))
      localStorage.setItem("thuTask", JSON.stringify(this.thuTask))
      localStorage.setItem("friTask", JSON.stringify(this.friTask))
      localStorage.setItem("satTask", JSON.stringify(this.satTask))
    },
    fetchData() {
      this.tasknumber = JSON.parse(localStorage.getItem("taskNumber") || 0)
      this.sunTask = JSON.parse(localStorage.getItem("sunTask") || "[]")
      this.monTask = JSON.parse(localStorage.getItem("monTask") || "[]")
      this.tueTask = JSON.parse(localStorage.getItem("tueTask") || "[]")
      this.wedTask = JSON.parse(localStorage.getItem("wedTask") || "[]")
      this.thuTask = JSON.parse(localStorage.getItem("thuTask") || "[]")
      this.friTask = JSON.parse(localStorage.getItem("friTask") || "[]")
      this.satTask = JSON.parse(localStorage.getItem("satTask") || "[]")
    },
    clearDataStorage() {
      localStorage.removeItem("taskNumber")
      localStorage.removeItem("sunTask")
      localStorage.removeItem("monTask")
      localStorage.removeItem("tueTask")
      localStorage.removeItem("wedTask")
      localStorage.removeItem("thuTask")
      localStorage.removeItem("friTask")
      localStorage.removeItem("satTask")
      this.fetchData()
    },
    linkToHome() {
      this.$router.push("/")
    },
    compare(a, b) {
      if (a.date < b.date) {
        return -1
      }
      if (a.date > b.date) {
        return 1
      }
      return 0
    },
  },
}
</script>

<style lang="scss">
textarea {
  padding: 0.5rem;
}

html {
  background-color: whitesmoke;
}

.sorry--section {
  display: block;
}

.sad-icon--container {
  display: flex;
  justify-content: center;
}

.sad--icon {
  font-size: 12rem;
}

.sorry-page-back-to-home-btn {
  display: flex;
  margin-left: 15rem;
  margin-right: 15rem;
  justify-content: center;
  background-color: #3778c2;
  border-style: solid;
  border-color: #3778c2;
  border-width: 2px;
  border-radius: 6px;
  padding: 0.75rem 1.5rem;
  color: white;
  &:hover {
    cursor: pointer;
    background: whitesmoke;
    color: #3e4c59;
  }
}

.to-do-page {
  display: none;
  background-color: rgba($color: #3778c2, $alpha: 0.05);
}
.to-do-page--intro-section {
  background-color: #3778c2;
  padding-top: 4rem;
  padding-bottom: 3rem;
}

.task-list--icon {
  margin-left: 3px;
  padding-bottom: 2px;
  font-size: 10rem;
  display: inline;
}

.intro-icon {
  display: flex;
  justify-content: center;
  color: white;
  font-size: 1.5rem;
}

.intro-text {
  display: flex;
  justify-content: center;
  color: white;
  font-size: 1.5rem;
}

.intro-description {
  display: flex;
  justify-content: center;
  color: white;
  font-size: 0.95rem;
}

.intro-btn {
  display: flex;
  justify-content: center;
}

.back-to-home-btn {
  background-color: white;
  border-style: solid;
  border-color: white;
  border-width: 2px;
  border-radius: 6px;
  padding: 0.75rem 1.5rem;
  margin-right: 1.5rem;
  font-weight: 500;
  &:hover {
    cursor: pointer;
    background: whitesmoke;
    color: #3e4c59;
  }
}

.clear-local-btn {
  color: white;
  border-style: solid;
  border-color: white;
  border-width: 2px;
  border-radius: 6px;
  padding: 0.75rem 1.5rem;
  font-weight: 500;
  &:hover {
    cursor: pointer;
    background: #f76d6d;
    border-color: none;
    color: #3e4c59;
  }
}

.to-do-page {
  background-color: rgba($color: #3778c2, $alpha: 0.05);
  font-size: 0.9rem;
}

.to-do-page--card-box {
  display: flex;
  padding: 2rem 0;
  justify-content: center;
}

.to-do-page--add-card-topic {
  display: flex;
  justify-content: center;
  font-size: 1rem;
  font-weight: 600;
}

.to-do-page--add-card {
  width: 16%;
  min-height: 100%;
  padding: 1rem;
  background-color: white;
  border: 2px solid #829ab1;
  border-radius: 6px;
  margin-right: 2.2rem;
}

.to-do-page--add-card-input-topic {
  margin-top: 1rem;
}

.input-topic {
  border: 1px solid #ecedee;
  border-radius: 6px;
  height: 36px;
  width: 80%;
  padding-left: 5px;
  margin-left: 10px;
}

.input-description {
  border: 1px solid #ecedee;
  border-radius: 6px;
  margin-top: 0.25rem;
  width: 98%;
  height: 100px;
}

.input-date.form-control.input {
  border: 1px solid #ecedee;
  border-radius: 6px;
  margin-top: 0.25rem;
  height: 36px;
  width: 80%;
  padding-left: 5px;
  margin-left: 14px;
}

.to-do-page--add-card-input-urgent {
  display: flex;
}

.urgent-text {
  margin-top: 5px;
  margin-left: 10px;
}

.to-do-page--add-card-add-btn-containter {
  display: flex;
  justify-content: center;
}

.add-btn {
  width: 100%;
  text-align: center;
  color: #1abc9c;
  border: #1abc9c;
  border-style: solid;
  border-width: 1px;
  border-radius: 6px;
  padding: 0.75rem 1.5rem;
  margin-right: 5px;
  &:hover {
    cursor: pointer;
    color: white;
    background-color: #1abc9c;
    box-shadow: 1px 5px 15px 5px #ededed;
  }
}

.to-do-page--show-card {
  width: 80%;
  min-height: 100%;
  padding: 1rem;
  background-color: white;
  border: 1px solid #ecedee;
  border-radius: 6px;
}

.day-flex-center {
  display: flex;
  justify-content: center;
  font-weight: 500;
}

.mon-task,
.tue-task,
.wed-task,
.thu-task,
.fri-task,
.sat-task {
  border-left: 1px solid #e8e8e8;
}

.sun-task {
  padding-top: 10px;
  background-color: #ffeeee;
  border-radius: 6px;
}

.mon-task {
  padding-top: 10px;
  background-color: #fffcf3;
  border-radius: 6px;
}

.tue-task {
  padding-top: 10px;
  background-color: #fef0f7;
  border-radius: 6px;
}

.wed-task {
  padding-top: 10px;
  background-color: #f6faf4;
  border-radius: 6px;
}

.thu-task {
  padding-top: 10px;
  background-color: #fdf1e9;
  border-radius: 6px;
}

.fri-task {
  padding-top: 10px;
  background-color: #f2f7fc;
  border-radius: 6px;
}

.sat-task {
  padding-top: 10px;
  background-color: #f4edf9;
  border-radius: 6px;
}

.task-card {
  display: block;
  margin: 10px 5px;
  padding: 10px;
  border: 1px solid #ecedee;
  background: white;
  border-radius: 6px;
  &:hover {
    color: #568be4;
    border: 1px solid #568be4;
  }
}

.task-card--topic {
  color: #568be4;
  display: flex;
  font-weight: 500;
  font-size: 0.85rem;
  justify-content: space-between;
}

.card-topic {
  display: flex;
}

.fire--icon {
  margin-left: 0.5rem;
  font-size: 1.1rem;
}

.trash--icon {
  font-size: 1.1rem;
  color: #f76d6d;
  &:hover {
    cursor: pointer;
    color: #e74c3c;
  }
}

.task-card--description {
  font-weight: 300;
  font-size: 0.7rem;
}

.task-card--footer {
  display: flex;
  justify-content: space-between;
  text-align: right;
  font-weight: 400;
  font-size: 0.65rem;
}

.finish-checkbox {
  display: flex;
}

.finish-card {
  color: #e8e8e8;
  &:hover {
    color: #e8e8e8;
    border: 1px solid #e8e8e8;
  }
  & > .task-card--topic {
    color: #e8e8e8;
  }
}

// Small devices (landscape phones, 576px and up)
@media screen and (min-width: 576px) {
}

// Medium devices (tablets, 768px and up)
@media screen and (min-width: 768px) {
}

// Large devices (desktops, 992px and up)
@media screen and (min-width: 992px) {
}

// Extra large devices (large desktops, 1200px and up)
@media screen and (min-width: 1200px) {
  html {
  background-color: white;
}
  .to-do-page {
    display: block;
  }
  .sorry--section {
  display: none;
}
}
</style>
