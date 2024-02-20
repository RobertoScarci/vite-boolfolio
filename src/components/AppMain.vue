<template lang="">
    <main class="container">
        <section class="row">
            <div class="col-10">
                <h1 class="text-center">
                    All My Projects:
                </h1>
                <ul class="text-center">

                    <li v-for="project in projects" :key="projects.id">
                        {{ project.title }} - {{ project.author }} - {{ project.date }}
                    </li>
                </ul>

            </div>
        </section>
    </main>
</template>

<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data(){
        return{
            projects: [],
        }
    },
    methods:{
        getProjects(){
            axios.get('http://127.0.0.1:8000/api/projects', {
                params: {
                }
            })
            .then((response) => {
                console.log(response.data.results.data);
                this.projects = response.data.results.data;
            })
            .catch(function (error) {
                console.warn(error);
            })
        }
    },
    created(){
        this.getProjects();
    }
}
</script>

<style lang="scss" scoped>
li{
    font-size: 20px;
    list-style-type: none;
}

</style>