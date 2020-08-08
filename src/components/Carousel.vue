<template>
    <div>
        <b-carousel
        id="carousel-1"
        v-model="slide"
        :interval="4000"
        controls
        indicators
        background="#ababab"
        img-width="1024"
        img-height="460"
        style="text-shadow: 1px 1px 2px #333;"
        @sliding-start="onSlideStart"
        @sliding-end="onSlideEnd"
        >
        <b-carousel-slide v-for="carouselItem in carouselItems" :key="carouselItem.id">
            <template v-slot:img>
                <img
                    class="d-block img-fluid w-100"
                    width="1024"
                    height="460"
                    :src="carouselItem.image"
                    alt="carouselItem.title"
                >
                <div class="carousel-centre">
                    <h1>BOOKING GREAT FILMS AND EVENTS</h1>
                    <div class="input-group mb-3">
                        <b-form-select :value="null" :options="null">
                             <b-form-select-option :value="null">CINEMAS</b-form-select-option>
                        </b-form-select>
                        <b-form-select :value="null" :options="null">
                             <b-form-select-option :value="null">FILMS</b-form-select-option>
                        </b-form-select>
                        <b-form-select :value="null" :options="null">
                             <b-form-select-option :value="null">DATES</b-form-select-option>
                        </b-form-select>
                        <b-form-select :value="null" :options="null">
                             <b-form-select-option :value="null">TIMES</b-form-select-option>
                        </b-form-select>
                        <b-button squared class="search-button"><b-icon icon="search"></b-icon></b-button>
                    </div>
                </div>
            </template>
            <h1>{{ carouselItem.title.toUpperCase() }}</h1>
            <h4>{{ carouselItem.sub_title }}</h4>
            <p>{{ carouselItem.text }}</p>
            <a :href="carouselItem.button_link" class="btn btn-light">{{carouselItem.button_name }}</a>
        </b-carousel-slide>

        </b-carousel>
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        data() {
            return {
                carouselItems: {},
                slide: 0,
                sliding: null
            }
        },
        mounted () {
            this.getCarouselDetails()
        },
        methods: {
            async getCarouselDetails() {
                const carousel = await axios.get('http://testvue.thetunagroup.com/?api=sliders')
                this.carouselItems = carousel.data.sliders
            },
            onSlideStart() {
                this.sliding = true
            },
            onSlideEnd() {
                this.sliding = false
            }
        }
    }
</script>

<style lang="css">
    .carousel .carousel-caption {
        text-align: left;
    }
    .carousel.slide {
        margin-top:-76px
    }
    .carousel-centre {
        position: absolute;
        right: 15%;
        top: 30%;
        left: 15%;
        z-index: 10;
        padding-top: 20px;
        padding-bottom: 20px;
        color: #fff;
        text-align: left;
    }
    .search-button {
        margin-left: 10px;
    }
</style>