<!-- Using the Composition API, long version -->

<script>
import {ref} from 'vue';

export default {
  setup() {
    const name = ref('John Doe');
    const status = ref('pending');
    const tasks = ref(['Task One', 'Task Two', 'Task Three']);
    const link = ref('https://google.com');

    const toggleStatus = () => {
      if (status.value === 'active') {
        status.value = 'pending';
      } else if (status.value === 'pending') {
        status.value = 'inactive';
      } else {
        status.value = 'active';
      }
    };

    return {
      name,
      status,
      tasks,
      link,
      toggleStatus
    };
  }
}
</script>

<template>
	<h1>{{ name }}</h1>
	<p v-if="status === 'active'">User is active</p>
	<p v-else-if="status === 'pending'">User is pending</p>
	<p v-else>User is not active</p>

	<h3>Tasks:</h3>
	<ul>
		<li v-for="task in tasks" :key="task">{{ task }}</li>
	</ul>

	<!-- <a v-bind:href="link">Click for Google</a> -->
	<a :href="link">Click for Google</a>
  
  <br/>
	
  <!-- <button v-on:click="toggleStatus">Change Status</button> -->
	<button @click="toggleStatus">Change Status</button>
</template>
