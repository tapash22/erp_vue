<template>
  <div class="texte">
    <!-- <Transition name="fade" mode="out-in"> -->
    <div>
      <transition mode="out" enter-active-class="animate__animated animate__zoomIn animate__faster"
        leave-active-class="animate__animated animate__zoomOut animate__fast">

        <div v-if="showNewInput" class="editpop">
          <vue-editor v-model="content" placeholder="Write comment here" :editor-toolbar="customToolbar" />

          <div class="d-flex justify-start pa-2 red">
            <v-btn @click="showNewInput = false" color="white"
              class="red--text text-body-2 font-weight-normal pa-2 rounded-lg">
              submit comment
            </v-btn>
          </div>
        </div>
      </transition>

      
        <div v-if="!showNewInput">
          <input type="text" class="icon-rtl" placeholder="Click to add comment here" @click="openText" />
        </div>
      

    </div>
    <!-- </Transition> -->
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

.icon-rtl {

  background: url("https://w7.pngwing.com/pngs/345/390/png-transparent-check-mark-computer-icons-circle-circle-thumbnail.png") no-repeat right white;
  background-size: 20px;
  padding-right: 50px;
}
</style>
