<template>
  <section class="all">
    <div>
      <navegation />
      <hprofile />

      <div class="buttons">
        <button @click="showComponent('profile')">Profile</button>
        <button @click="showComponent('team')">Team</button>
        <button @click="showComponent('connections')">Connections</button>
        <button @click="showComponent('project')">Projects</button>
      </div>

      <div v-if="currentComponent === 'profile'">
        <profile />
      </div>
      <div v-if="currentComponent === 'team'">
        <Team />
      </div>
      <div v-if="currentComponent === 'connections'">
        <Connections />
      </div>
      <div v-if="currentComponent === 'project'">
        <project />
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { ref } from 'vue'; 

import navegation from './components/navegation.vue';
import hprofile from './components/hprofile.vue';
import profile from './components/profile.vue';
import Team from './components/team.vue';
import Connections from './components/connections.vue';
import project from './components/project.vue';

export default {
  components: {
    navegation,
    hprofile,
    profile,
    Team,
    Connections,
    project
  },
  setup() {
    const currentComponent = ref<string>('profile');

    const showComponent = (component: string) => {
      currentComponent.value = component;
    };

    return {
      currentComponent,
      showComponent
    };
  }
}
</script>

<style scoped>
.buttons {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
  padding-top: 20px;
}

button {
  padding: 10px 20px;
  border: none;
  background-color: #7f7fd5;
  color: white;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background-color: #5c5c9b;
}
.all {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    padding-left: 15%;
    padding-right: 15%;
  }
</style>