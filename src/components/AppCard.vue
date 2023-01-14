<script>
export default {
    props: {
        character: Object
    }
}
</script>
<template lang="">
    <div class="card text-center mb-3">
        <div class="img">
            <img :src="character.card_images[0].image_url" :alt="character.name">
        </div>
        <div class="info">
            <span>{{ character.name }}</span> 
            <span>{{ character.archetype }}</span>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.card {
    width: calc(100% / 5 - 20px);
    background-color: #d48f38;

}

span:first-child {
    text-transform: uppercase;
    color: white;
    font-weight: bold;

}

img {
    width: 100%;
    object-fit: contain;
}

.info span {
    display: block;
}
</style>