<template>
  <div>
    <div class="comment-list">
      <v-btn icon @click="openEmoji = !openEmoji">
        <v-icon size="18" color="gray"> mdi-emoticon-happy-outline </v-icon>
      </v-btn>

      <v-btn
        @click="showInput = true"
        icon
        class="text-body-1 font-weight-normal text-decoration-underline mx-2 py-0 font"
      >
        Reply
      </v-btn>
      <v-btn
        @click="removeTextBox"
        icon
        class="text-body-1 font-weight-normal text-decoration-underline mx-2 py-0 font"
      >
        Delete
      </v-btn>
      <v-btn icon class="text-body-1 font-weight-normal mx-2 py-0 font">
        <v-icon size="18" color="blue"> mdi-paperclip </v-icon>
      </v-btn>
      <span class="pt-3 font-weight-bold text-sm">5</span>
    </div>

    <div>
      <transition mode="out" enter-active-class="animate__animated animate__zoomIn animate__faster"
        leave-active-class="animate__animated animate__zoomOut animate__fast">
      <v-list-item-subtitle v-if="showInput">
        <TextEditor3 />
        <div v-if="showNewInput" style="display: block"></div>
      </v-list-item-subtitle>
</transition>
    </div>
    <div v-if="openEmoji" class="emoji">
      <Emoji />
    </div>
  </div>
</template>

<script>
import Emoji from "./Emoji.vue";
import TextEditor3 from "../texteditor/TextEditor3.vue";

export default {
  data() {
    return {
      show: true,
      showNewInput: false,
      showInput: false,
      openEmoji: false,
    };
  },
  mounted() {
    this.showNewInput = false;
  },

  components: {
    Emoji,
    TextEditor3,
  },

  methods: {
    openText() {
      this.showNewInput = true;
      this.show = false;
    },

    removeTextBox() {
      this.showInput = false;
      // this.showNewInput = !this.showNewInput;
    },
  },
};
</script>

<style scoped>
.comment-list {
  display: grid;
  grid-template-columns: 30px 60px 60px 40px 30px;
}

.emoji {
  position: absolute;
  height: 100px;
  z-index: 99;
}

input {
  width: 100%;
  background: #fff;
  padding: 10px;
  box-shadow: 0 0 2px gray;
  border-radius: 5px;
  font-size: 14px;
  font-weight: 500;
}
</style>
