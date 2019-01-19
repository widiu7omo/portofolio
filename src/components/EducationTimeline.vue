<template>
    <v-timeline transition="slide-x-transition">
        <v-timeline-item v-for="edu in education" :key="edu.title" color="red lighten-2" large>
            <span slot="opposite">{{edu.status}}</span>
            <v-card class="elevation-2" >
                <v-card-title class="headline text-truncate">{{edu.title}}</v-card-title>
                <v-card-text>
                    <span><i class="font-weight-light">{{edu.year}}, </i></span>
                    <span>{{edu.schoolname}}</span>
                </v-card-text>
            </v-card>
        </v-timeline-item>
    </v-timeline>
</template>
<script>
    export default {
        data() {
            return {
                education:[
                    {title:'Senior High School',
                    status:'Graduated',
                    schoolname:'MAN Trenggalek',
                    year:'2010 - 2013'},
                    {title:'University',
                    status:'In college',
                    schoolname:'State of Polytechnic Tanah Laut',
                    year:'2016 - 2019'}
                ]
            }
        },
    }
</script>
<style scoped>

</style>