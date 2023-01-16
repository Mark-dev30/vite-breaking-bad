<script>
import { store } from '../store'
export default {

    data() {
        return {
            changeType: "",
            store
        }
    },
    methods: {

    },
}
</script>
<template lang="">
    <div class="row margin-auto">
        <div class="col-8">
            <select name="race" id="race" v-model="changeType" @change="$emit('search', changeType)">
                <option value="Continuous">Continuous</option>
                <option value="Quick-Play">Quick-Play</option>
                <option value="Reptile">Reptile</option>
                <option value="Normal">Normal</option>
            </select>
        </div>
    </div>
</template>
<style lang="scss" scoped>
.margin-auto {
    width: 90%;
    margin: 0 auto;
    margin-top: 30px;


    select {
        width: 150px;
        padding: 5px;
        border-radius: 0.4rem;
        margin-top: 30px;
    }
}
</style>