<template>
    <section>
        <div id="particles-js"></div>
        <div class="btn-start"></div>
    </section>
</template>
<style lang="scss" scope>
    .btn-start{

    }
</style>
<script>
    import {pJS} from '../assets/js/particles.js'
    console.log(particlesJS)
    console.log(pJS)
    export default {
        data(){
          return {
              particles:{
                "particles": {
                "number": {
                    "value": 30,
                        "density": {
                        "enable": true,
                            "value_area": 800
                    }
                },
                "color": {
                    "value": "#888"
                },
                "shape": {
                    "type": "circle",
                        "stroke": {
                        "width": 0,
                            "color": "#000000"
                    },
                    "polygon": {
                        "nb_sides": 5
                    },
                    "image": {
                        "src": "img/github.svg",
                            "width": 100,
                            "height": 100
                    }
                },
                "opacity": {
                    "value": 0.5,
                        "random": true,
                        "anim": {
                        "enable": false,
                            "speed": 1,
                            "opacity_min": 0.1,
                            "sync": true
                    }
                },
                "size": {
                    "value": 5,
                        "random": true,
                        "anim": {
                        "enable": false,
                            "speed": 40,
                            "size_min": 0.1,
                            "sync": false
                    }
                },
                "line_linked": {
                    "enable": true,
                        "distance": 150,
                        "color": "#333",
                        "opacity": 0.4,
                        "width": 1
                },
                "move": {
                    "enable": true,
                        "speed": 6,
                        "direction": "none",
                        "random": false,
                        "straight": false,
                        "out_mode": "out",
                        "attract": {
                        "enable": false,
                            "rotateX": 1200,
                            "rotateY": 600
                    }
                }
            },
                "interactivity": {
                "detect_on": "canvas",
                    "events": {
                    "onhover": {
                        "enable": true,
                            "mode": "grab"
                    },
                    "onclick": {
                        "enable": true,
                            "mode": "push"
                    },
                    "resize": true
                },
                "modes": {
                    "grab": {
                        "distance": 150,
                            "line_linked": {
                            "opacity": 1
                        }
                    },
                    "bubble": {
                        "distance": 400,
                            "size": 40,
                            "duration": 2,
                            "opacity": 8,
                            "speed": 3
                    },
                    "repulse": {
                        "distance": 200
                    },
                    "push": {
                        "particles_nb": 2
                    },
                    "remove": {
                        "particles_nb": 2
                    }
                }
            },
                "retina_detect": true,
                "config_demo": {
                "hide_card": false,
                    "background_color": "#b61924",
                    "background_image": "",
                    "background_position": "50% 50%",
                    "background_repeat": "no-repeat",
                    "background_size": "cover"
            }
            }
          }
        },
        mounted(){
            particlesJS('particles-js',this.particles);
        }
    }

</script>