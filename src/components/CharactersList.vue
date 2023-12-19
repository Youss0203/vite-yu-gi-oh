<template lang="">
    <section id="card" class="container">
        <div class="row">
        <article v-for="character in charactersList" class="container mb-5">
            <img :src="character.card_images[0].image_url" alt="">
        <h5 class="text-center">{{character.name}}</h5>
        <p class="text-center">{{character.archetype}}</p>
        </article>
        </div>
    </section>
</template>
<script>
import {store} from '../js/store.js';
export default {
    data() {
        return {
            store,
        }
    },
    props:{
        charactersList:{
            type:Object,
            required:true,
        }
    }
}
</script>
<style lang="scss" scoped>
section{
    background-color: white;
    padding: 2rem;
}
article{
    width: calc((100% / 5) - 1rem);
    margin-right: .5rem;
    margin-left: .5rem;
    background-color: #d48f38;

    img{
        width: 100%;
    }

    h5{
        color:white;
    }
}
</style>