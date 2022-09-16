<template>
  <section class="filter-controls">
    <label>
      <input type="checkbox" value="Programmering" v-model="selectedFields" />
      Programmering
    </label>
    <label>
      <input type="checkbox" value="Web-development" v-model="selectedFields" />
      Web-development
    </label>
    <label>
      <input type="checkbox" value="Networking" v-model="selectedFields" />
      Networking
    </label>
    <label>
      <input type="checkbox" value="Diploma Project" v-model="selectedFields" />
      Diploma Project
    </label>
    <label>
      <input type="checkbox" value="Physics" v-model="selectedFields" /> Physics
    </label>
    <label>
      <input type="checkbox" value="Math" v-model="selectedFields" /> Math
    </label>
    <label>
      <input type="checkbox" value="Swedish" v-model="selectedFields" /> Swedish
    </label>
    <label>
      <input type="checkbox" value="English" v-model="selectedFields" /> English
    </label>
    <label>
      <input type="checkbox" value="Spanish" v-model="selectedFields" /> Spanish
    </label>
    <button @click="filter()">Search</button>
  </section>
  <section>
    <div v-for="teacher in filteredList">
      <h2>{{ teacher.name }}</h2>
      <ul>
        <li v-for="subject in teacher.subjects">
          {{ subject.name }} : {{ subject.level }}
        </li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      filteredList: [],
      selectedFields: [],
      teachers: [
        {
          name: "Sebastian Jensen",
          subjects: [
            {
              name: "Programming",
              level: "9th",
            },
            {
              name: "Web-development",
              level: "High school",
            },
          ],
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
        },
        {
          name: "Anders",
          subjects: [
            {
              name: "Swedish",
              level: "High school",
            },
            {
              name: "Spanish",
              level: "High school",
            },
          ],
        },
        {
          name: "Lars",
          subjects: [
            {
              name: "Math",
              level: "First- to Sixth grade",
            },
          ],
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
        },
      ],
    };
  },
  methods: {
    filter() {
      this.teachers.forEach((teacher) => {
        teacher.subjects.forEach((subject) => {
          if (this.selectedFields.includes(subject.name)) {
            console.log(this.filteredList);
            console.log(Array.isArray(this.filteredlist));
            this.filteredList.push({
              name: teacher.name,
              subjects: [
                {
                  name: subject.name,
                  level: subject.level,
                },
              ],
            });
          }
        });
      });
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
}

.filter-controls {
  margin: 10px;
}
</style>
