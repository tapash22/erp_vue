<template>
  <v-card class="my-1 rounded-lg">
    <v-card-title class="rounded-tl-lg rounded-tr-lg d-flex justify-start font font1 card-t">
      {{ detail.title }}
    </v-card-title>
    <v-card-text class="overflow-scroll pa-2 font font2 card-text">
      {{ formattedBody }}
      <v-btn text @click="showingFullText = !showingFullText" class="blue--text pa-0 text-decoration-none">
        {{ readMoreText }}
      </v-btn>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  props: ["detail"],

  data() {
    return {
      showingFullText: false,
      text: this.detail.text,
    };
  },

  computed: {
    formattedBody() {
      if (!this.showingFullText) {
        return this.text.slice(0, 500);
      }
      return this.text;
    },

    readMoreText() {
      return this.showingFullText ? ' ' : 'Read full guideline'
    }
  },
};
</script>

<style scoped>
.card-t {
  background: #e7effc;
}

.font1 {
  font-size: 16px;
  font-weight: 400;
  color: #777777;
}

.font2 {
  font-size: 14px;
}

.card-text {
  height: 171px;
  overflow-y: auto;
}
</style>