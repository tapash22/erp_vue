<template>
  <div class="texte">
    <transition mode="out" enter-active-class="animate__animated animate__zoomIn animate__faster"
        leave-active-class="animate__animated animate__zoomOut animate__fast">

    <div v-if="showNewInput" class="editpop">
      <vue-editor
        v-model="content"
        placeholder="Write reply here"
        :editor-toolbar="customToolbar"
      />

      <div class="d-flex justify-start pa-2 red">
        <v-btn
          @click="showNewInput = false"
          color="white"
          class="red--text text-body-2 font-weight-normal pa-2 rounded-lg"
        >
          submit comment
        </v-btn>
      </div>
    </div>
    </transition>

    <div class="w-full" v-if="!showNewInput">
      <input
        type="text"
        placeholder="Click to add reply here"
        @click="openText"
      />
    </div>
  </div>
</template>

<script>
import { VueEditor } from "vue2-editor";

export default {
  components: { VueEditor },

  data: () => ({
    showNewInput: false,

    content: "",
    customToolbar: [
      ["bold", "italic", "underline"],
      [{ list: "ordered" }, { list: "bullet" }],
      ["image", "code-block", "file"],
    ],
  }),

  methods: {
    closeEditor() {
      this.showNewInput = false;
    },

    openText() {
      this.showNewInput = true;
    },
  },
};
</script>

<style scoped>
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
