<template>
    <v-container grid-list-md>
        
        <p class="display-1"> Projects</p>
        <v-layout row wrap>
            <v-flex v-for="project in projects" :key="project.title" xs12 sm6 md4 lg3>
                <v-card>
                    <v-img :src="require(`@/assets/${project.pic}`)" height="200px">
                    </v-img>
                    <v-card-title primary-title>
                        <div>
                            <h3 class="headline mb-0">{{project.title}}</h3>
                            <div>{{project.desc}}</div>
                        </div>
                    </v-card-title>
                    <v-card-actions>
                        <v-btn flat color="primary">View</v-btn>
                        <v-btn flat color="primary">Quick View</v-btn>
                    </v-card-actions>
                </v-card>
            </v-flex>
        </v-layout>
    </v-container>
</template>
<script>
    export default {
data() {
    return {
        projects:[
            {title:'Phinemo Marketplace',
            desc:'The marketplace that focuses on tour traveler, who provide many services and tour guide in Indonesia. There are many package trip that we can take from it.',
            pic:'phinemo.png'}
        ]
    }
},
    }
</script>
<style scoped>

</style>