<template>
<v-expansion-panels focusable>
    <v-expansion-panel>
        <v-expansion-panel-header class="white--text font font1" color="red darken-2">
            <template v-slot:actions>
                <v-icon color="red"> $expand </v-icon>
            </template>
            {{ detail.title }}</v-expansion-panel-header>
        <v-expansion-panel-content class="light light2 my-2">
            <div class="card-border " v-for="ct in detail.lists" :key="ct.id">
                <!-- {{ ct }} -->
                <CardSingle :ct="ct"/>
            </div>
        </v-expansion-panel-content>
    </v-expansion-panel>
</v-expansion-panels>
</template>

<script>
import CardSingle from './CardSingle.vue';
 
export default {
    props: ["detail"],

    components:{
      CardSingle
    }
};
</script>

<style>
.v-expansion-panel-header__icon {
    color: #f30505 !important;
    width: 30px !important;
    height: 30px !important;
    border-radius: 50% !important;
    background: white !important;
    display: flex;
    justify-content: center;
}

.font1 {
    font-size: 16px;
    font-weight: 400;
    color: #777777;
}

.card-border {
    box-shadow: 0 0 5px blue;
    margin-top: 5px;
    border-radius: 10px;
}

.light2 {
    height: 171px;
    padding-bottom: 5px;

    overflow-y: scroll;
    overflow-x: hidden;
}

.light::-webkit-scrollbar {
    width: 10px;
}

.light::-webkit-scrollbar-track {
    background: #e6e6e6;
    border-left: 1px solid #dadada;
}

.light::-webkit-scrollbar-thumb {
    background: #616e80;
    border: solid 3px #e6e6e6;
    border-radius: 7px;
}

.light::-webkit-scrollbar-thumb:hover {
    background: #616e80;
}


</style>
