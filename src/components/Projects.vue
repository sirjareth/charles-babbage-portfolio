<template>
	<!-- My Projects -->
	<section class="pb-5" id="projects">
	    <h1 class="mt-5 mb-5 pb-4 text-center">My Projects</h1>
	    
	    <div
	    	v-for="(group, index) in chunkedProjects"
	    	:key="index"
	    	class="card-deck my-5 justify-content-center"
	    >
	    	<ProjectCard
	    		v-for="project in group"
	    		:key="project.id"
	    		:project="project"
	    	/>
	    </div>
	</section>
</template>

<script setup>
	import { computed } from 'vue';

	import ProjectCard from './ProjectCard.vue';

	import projects from '../data/projects.json';

	const chunckSize = 3;

	const chunkedProjects = computed(() => {
		const chuncks = [];

		for (let i = 0; i < projects.length; i += chunckSize){
			chuncks.push(projects.slice(i, i + chunckSize));
		}

		return chuncks;
	})
</script>