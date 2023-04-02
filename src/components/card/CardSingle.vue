<template>
    <div>
        <div class="d-block d-md-flex pa-2">
            <div class="pa-2 indigo lighten-5 rounded-lg d-flex justify-space-between align-center d-md-block box3">
                <span class="red--text text-h6">{{ ct.number }}</span>
                <div class="text-caption">
                    <span class="text-caption font-weight-bold">Date:</span>{{ ct.date }}
                </div>
                <div class="text-caption">
                    <span class="text-caption font-weight-bold">Time:</span>{{ ct.time }}
                </div>
            </div>

            <div class="pa-2 font font2 box2 text-justify ">{{ ct.text1 }}</div>
        </div>

        <div class="pa-4 font font2 text-justify">
            <!-- {{ ct.text2 }} -->
            {{ formattedBody }}
            <v-btn text @click="showingFullText = !showingFullText"  class="blue--text pa-0 text-decoration-none">
                {{readMoreText}}
            </v-btn>
        </div>
    </div>
</template>

<script>
export default {
    props: ["ct"],

    data() {
        return {
            showingFullText: false,
            text: this.ct.text2,
        }
    },


    computed: {
        formattedBody() {
            if (!this.showingFullText) {
                return this.text.slice(0, 200);
            }
            return this.text;
        },

        readMoreText() {
      return this.showingFullText ? ' ' : 'Read full guideline'
    }
    },

}
</script>

<style>
.box3 {
    width: 15%;
    height: 100px;
}

.box2 {
    width: 85%;
}

.font2 {
    font-size: 14px;
    color: #777777;
}

@media only screen and (max-width: 600px) {
    .box2 {
        width: 100%;
    }

    .box3 {
        width: 100%;
        height: auto;
    }

    .btn {
        display: flex;
        justify-content: center;
    }
}
</style>