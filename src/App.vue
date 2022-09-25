<template>
  <section class="filter-controls">
    <section class="subject-filter-controls">
      <h2>Subjects</h2>
      <label>
        <input type="checkbox" value="Programmering" v-model="selectedFields" />
        Programmering
      </label>
      <label>
        <input
          type="checkbox"
          value="Web-development"
          v-model="selectedFields"
        />
        Web-development
      </label>
      <label>
        <input type="checkbox" value="Networking" v-model="selectedFields" />
        Networking
      </label>
      <label>
        <input
          type="checkbox"
          value="Diploma Project"
          v-model="selectedFields"
        />
        Diploma Project
      </label>
      <label>
        <input type="checkbox" value="Physics" v-model="selectedFields" />
        Physics
      </label>
      <label>
        <input type="checkbox" value="Math" v-model="selectedFields" /> Math
      </label>
      <label>
        <input type="checkbox" value="Swedish" v-model="selectedFields" />
        Swedish
      </label>
      <label>
        <input type="checkbox" value="English" v-model="selectedFields" />
        English
      </label>
      <label>
        <input type="checkbox" value="Spanish" v-model="selectedFields" />
        Spanish
      </label>
    </section>
    <section class="year-filter-controls">
      <h2>Year:</h2>
      <label>
        <input type="checkbox" value="1" v-model="selectedFields" /> 1
      </label>
      <label>
        <input type="checkbox" value="2" v-model="selectedFields" /> 2
      </label>
      <label>
        <input type="checkbox" value="3" v-model="selectedFields" /> 3
      </label>
      <label>
        <input type="checkbox" value="4" v-model="selectedFields" /> 4
      </label>
      <label>
        <input type="checkbox" value="5" v-model="selectedFields" /> 5
      </label>
      <label>
        <input type="checkbox" value="6" v-model="selectedFields" /> 6
      </label>
      <label>
        <input type="checkbox" value="7" v-model="selectedFields" /> 7
      </label>
      <label>
        <input type="checkbox" value="8" v-model="selectedFields" /> 8
      </label>
      <label>
        <input type="checkbox" value="9" v-model="selectedFields" /> 9
      </label>
      <label>
        <input type="checkbox" value="10" v-model="selectedFields" /> 10
      </label>
      <label>
        <input type="checkbox" value="11" v-model="selectedFields" /> 11
      </label>
      <label>
        <input type="checkbox" value="12" v-model="selectedFields" /> 12
      </label>
    </section>
  </section>

  <button class="searchButton" @click="filter()">Search</button>
  <section class="teacherContainer">
    <div v-for="teacher in filteredList" class="teacher">
      <h2>{{ teacher.name }}</h2>
      <ul>
        <li v-for="subject in teacher.subjects">
          {{ subject.name }} : {{ subject.level }}
        </li>
      </ul>
    </div>
  </section>
  <!-- {{ selectedFields }} -->
</template>

<script>
export default {
  data() {
    return {
      selectedFields: [],
      filteredList: [],
      teachers: [
        {
          name: "Sebastian Jensen",
          subjects: [
            {
              name: "Programming",
              level: "Highschool",
            },
            {
              name: "Web-development",
              level: "Highschool",
            },
          ],
          years: [11, 10],
        },
        {
          name: "Liv Sundman",
          subjects: [
            {
              name: "Networking",
              level: "9th",
            },
            {
              name: "Diploma project",
              level: "Highschool",
            },
          ],
          years: [9, 12],
        },
        {
          name: "Mikael Bergström",
          subjects: [
            {
              name: "Programming",
              level: "High school",
            },
            {
              name: "Diploma Project",
              level: "High school",
            },
          ],
          years: [11, 10],
        },
        {
          name: "Simon",
          subjects: [
            {
              name: "Physics",
              level: "High school",
            },
            {
              name: "Math",
              level: "High school",
            },
          ],
          years: [11, 10],
        },
        {
          name: "Anders",
          subjects: [
            {
              name: "Swedish",
              level: "High school1",
            },
            {
              name: "Spanish",
              level: "High school2",
            },
          ],
          years: [11, 10],
        },
        {
          name: "Lars",
          subjects: [
            {
              name: "Math",
              level: "First- to Sixth grade",
            },
          ],
          years: [1, 2, 3, 4, 5, 6, 7, 8, 9],
        },
        {
          name: "Erina",
          subjects: [
            {
              name: "English",
              level: "First- to Ninth grade",
            },
            {
              name: "Swedish",
              level: "High school",
            },
          ],
          years: [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12],
        },
      ],
    };
  },
  methods: {
    filter() {
      this.filteredList = [];
      this.teachers.forEach((teacher) => {
        let teacherHasSubject = false;
        let teacherHasYear = false;
        let tempSubject = [];
        teacher.subjects.forEach((subject) => {
          if (this.selectedFields.includes(subject.name)) {
            teacherHasSubject = true;
            tempSubject.push({
              name: subject.name,
              level: subject.level,
            });
          }
        });
        teacher.years.forEach((year) => {
          if (this.selectedFields.includes(year.toString())) {
            teacherHasYear = true;
          }
        });
        if (teacherHasSubject && teacherHasYear) {
          this.filteredList.push({
            name: teacher.name,
            subjects: tempSubject,
          });
        }
      });
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
}

.subject-filter-controls {
  margin: 10px;
  display: grid;
}

.year-filter-controls {
  margin: 10px;
  display: grid;
}

.filter-controls {
  width: 100%;
  justify-content: space-evenly;
  display: flex;
  flex-direction: row;
}

.searchButton {
  margin-left: calc(50% - 10rem);
  width: 20rem;
  height: 2.5rem;
}

.teacherContainer {
  max-width: 33vw;
  min-width: 10rem;
  display: flex;
  gap: 1rem;
  margin: auto;
  flex-direction: column;
  margin-top: 2rem;
}

.teacher {
  width: 100%;
  min-height: 5rem;
  border: 1px solid #333;
  padding: 0.5rem;
}
</style>
