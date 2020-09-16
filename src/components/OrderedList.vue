<template>
  <div class="container">
    <main class="timeline">
      <li
        class="profile-card"
        v-for="profile in sortedArray"
        v-bind:key="profile._id"
      >
        <section class="profile">
          <section class="personal-info">
            <h3>{{ profile.name.first }} {{ profile.name.last }}</h3>
            <p>{{ profile.about }}</p>
            <ul>
              <li class="tags" v-for="tag in profile.tags" v-bind:key="tag">
                #{{ tag }}
              </li>
            </ul>
          </section>
          <section class="date">{{ profile.registered }}</section>
        </section>
      </li>
    </main>
  </div>
</template>

<script>
import json from "../assets/json/timeline.json";

export default {
  name: "OrderedList",
  data() {
    return {
      profileList: json,
    };
  },
  computed: {
    sortedArray: function() {
      return this.profileList.sort(
        (a, b) => new Date(a.registered) - new Date(b.registered)
      );
    },
  },
};
</script>

<style scoped>
.container {
  counter-reset: section;
}

p {
  line-height: 1.5;
}

.timeline {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  align-items: center;
  margin-left: 10%;
}

.timeline li {
  list-style-type: none;
}

.profile-card {
  width: 100%;
  margin-bottom: 20px;
}

.profile-card > ::before {
    counter-increment: section;
    content: counter(section);
    position: absolute;
    border-radius: 50%;
    padding: 10px;
    margin: 10px;
    height: 1.25em;
    width: 1.25em;
    background-color: rgba(6, 82, 117, 0.7);
    text-align: center;
    line-height: 1.25em;
    color: white;
    font-size: 1em;
}

.personal-info {
  background-color: rgba(87, 155, 187, 0.5);
  border-radius: 15px 15px 0 0;
  padding: 30px;
}

.tags {
  list-style-type: none;
  display: inline-block;
  margin-right: 20px;
}

.date {
  background-color: rgba(6, 82, 117, 0.7);
  width: 100%;
  padding: 10px;
  border-radius: 0 0 15px 15px;
  font-size: 14px;
  text-align: right;
  color: white;
}

/* tablet */
@media screen and (min-width: 541px) {
  .timeline {
    margin-left: 10%;
  }

  .profile-card {
    width: 60%;
  }

  .timeline > :nth-child(even){
    border-left: 3px solid rgba(6, 82, 117, 0.7);
    padding-left: 30px;
  } 

  .timeline > :nth-child(odd){
    border-right: 3px solid rgba(6, 82, 117, 0.7);
    padding-right: 30px;
    align-self: flex-start;
  } 
}

/* desktop */
@media screen and (min-width: 961px) {
  .timeline {
    margin-left: 15%;
  }

  .profile-card {
    width: 50%;
  }

  .timeline > :nth-child(even){
    margin-left: 15%;
  } 

  .timeline > :nth-child(odd){
    margin-right: 15%;
  } 
}
</style>
