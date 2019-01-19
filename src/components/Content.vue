<template>
    <v-container fluid class="background mt-5" grid-list-md>
        <v-layout id="introduce" align-center justify-center>
            <v-flex xs12 sm12 md6 lg6>
                <p class="display-1"> -- Hey there</p>
                <v-card class="elevation-7 terminal" height="400px" style="border-radius:4px;">
                    <v-system-bar class="elevation-2" window color="grey lighten-3">
                        <v-icon color="red lighten-1">fiber_manual_record</v-icon>
                        <v-icon color="yellow darken-1">fiber_manual_record</v-icon>
                        <v-icon color="light-green accent-4">fiber_manual_record</v-icon>
                        <v-spacer></v-spacer>
                    </v-system-bar>
                    <v-layout row wrap full-height class="terminal-content">
                        <v-card-text class="bash" d-inline-flex>
                            <span v-for="(bash,i) in arrayBash" :key="i">
                                <span v-html="bash.home"></span>
                                <span v-html="bash.text"></span><br>
                            </span>
                            <span class="hostname" v-html="initBash"></span>
                            <vue-typer :text="texts" 
                                initial-action='typing'
                                :pre-type-delay='1000'
                                :type-delay='150'
                                :pre-erase-delay='0'
                                :erase-delay='250'
                                erase-style='clear'
                                :erase-on-complete='true'
                                caret-animation='blink'
                                :repeat="0" 
                                @typed="onTyped" 
                                @completed='onComplete' 
                                style="position:absolute;left:66px"></vue-typer>
                        </v-card-text>
                    </v-layout>
                </v-card>
                <div class="mt-4">
                    For view my project, type <kbd>ls project</kbd> into your console. Or, type <kbd>ls about</kbd> to
                    view my detail profile
                </div>
            </v-flex>
        </v-layout>
        <v-layout id="education" align-center justify-center mt-3>
            <v-flex xs12 sm12 md6 lg6>
                <p class="display-1"> Education</p>
                <education-timeline></education-timeline>
            </v-flex>
        </v-layout>
        <v-layout align-center justify-center wrap id="skills">
            
        </v-layout>
        <v-layout row wrap id="project">
            <project></project>
        </v-layout>
    </v-container>
</template>
<script>
    function bashText({
        home,
        text
    }) {
        this.home = home;
        this.text = text;
    }
    import {
        VueTyper
    } from 'vue-typer'
    import educationTimeline from './EducationTimeline'
    import project from './Project'
    export default {
        data: () => ({
            initBash: "bash$&nbsp;",
            arrayBash: [],
            texts: ["Hey there, i'm danar. Nice to meet you", "I'm web developer, and focus on Backend Dev"],
            windowSize: {
                x: 0,
                y: 0
            },
            education:false,
        }),
        components: {
            VueTyper,
            educationTimeline,
            project
        },
        mounted() {

        },
        methods: {
            onComplete() {
                // console.log('done');
            },
            onTyped(typedString) {
                var objectBash = {
                    home: this.initBash,
                    text: typedString
                }
                this.arrayBash.push(new bashText(objectBash))
            },
            onResize() {
                this.windowSize={x:window.innerWidth,y:window.innerHeight}
                // if(window.innerWidth < 800){
                    
                // }
            }
        },
    }
</script>
<style scoped>
    .terminal {
        background-color: #ffffff57;
        position: relative;
    }

    .terminal-content {
        position: relative;
    }

    .background {
        /* background-color: silver */
        background: linear-gradient(132deg, #ec5218, #1665c1);
        background-size: 400% 400%;
        animation: BackgroundGradient 30s ease infinite;
    }

    @keyframes BackgroundGradient {
        0% {
            background-position: 0% 50%;
        }

        50% {
            background-position: 100% 50%;
        }

        100% {
            background-position: 0% 50%;
        }
    }

    @import url('https://fonts.googleapis.com/css?family=Roboto+Mono:500');

    .bash {
        font-family: 'Roboto Mono', monospace;
        position: relative;
        overflow: auto;
    }

    .hostname {
        position: absolute;
    }

    .vue-typer {
        font-family: 'Roboto Mono', monospace;
    }

    .vue-typer .custom.char.typed {
        color: #009688;
    }

    .vue-typer .custom.char.selected {
        color: #E91E63;
    }

    .vue-typer .custom.caret {
        animation: rocking 1s ease-in-out 0s infinite;
        /* display: inline-block; */
    }

    @keyframes rocking {

        0%,
        100% {
            transform: rotateZ(-10deg);
        }

        50% {
            transform: rotateZ(10deg);
        }
    }

    .vue-typer .custom.caret.typing {
        background-color: #009688;
    }

    .vue-typer .custom.caret.selecting {
        display: inline-block;
        background-color: #E91E63;
    }
</style>