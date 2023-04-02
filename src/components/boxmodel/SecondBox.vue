<template>
  <div>
    <v-card
      class="rounded-lg my-4 relative"
      color="white"
      v-for="content in content2"
      :key="content.id"
    >
      <v-card-title class="text-body-1 font-weight-bold">
        {{ content.name }}
      </v-card-title>
      <v-card-subtitle class="pa-1 d-flex justify-start">
        <v-btn icon @click="addComment = !addComment" class="ml-14">
          <v-icon color="#1D82F5" class="text-display-1">mdi-plus</v-icon>
          <span class="text blue--text">Add Comment</span>
        </v-btn>
      </v-card-subtitle>

      <!-- add comment -->
      <div>
        <v-dialog v-model="addComment" width="750px">
          <v-card class="pa-1" height="100%">
            <v-card-text>
              <v-list class="d-flex">
                <v-avatar size="62" class="pt-5 pr-2" color="black">
                  <v-img
                    src="https://freepngimg.com/thumb/man/22654-6-man-thumb.png"
                  />
                </v-avatar>
                <v-list-item class="dialog-box">
                  <TextEditor />
                  <UploadImage />
                  <!-- <EditorTwo /> -->
                </v-list-item>
              </v-list>
              <!-- <UploadImage /> -->
            </v-card-text>
          </v-card>
        </v-dialog>
      </div>

      <v-card-text class="rounded-lg pb-0 pt-0">
        <v-list class="pa-0" v-if="content.lists">
          <v-list-item
            class="pa-0 list-item"
            v-for="list in content.lists"
            :key="list.id"
          >
            <v-list-item-title class="text font pl-2">
              {{ list.text }}
            </v-list-item-title>
            <v-list-item-subtitle class="d-flex justify-end sub">
              <v-btn icon @click="showSingleComment = !showSingleComment">
                <v-icon class="text-body-1 px-2">{{ list.icon1 }}</v-icon>
              </v-btn>
              <v-btn icon @click="showSingleComment1 = !showSingleComment1">
                <v-icon class="text-body-1 px-2">{{ list.icon2 }}</v-icon>
              </v-btn>
            </v-list-item-subtitle>
          </v-list-item>
        </v-list>
      </v-card-text>

      <!-- sidebar icon -->
      <v-card-title class="tagg">
        <div>
          <v-btn icon @click="openDialog">
            <v-avatar size="24" color="blue">
              <v-icon
                color="white"
                class="text-body-1 font-weight-regular"
                v-if="isActive"
              >
                mdi-chevron-left
              </v-icon>
              <v-icon
                color="white"
                class="text-body-1 font-weight-regular"
                v-else
              >
                mdi-chevron-right
              </v-icon>
            </v-avatar>
          </v-btn>

          <v-dialog v-model="dialog" width="750px">
            <v-card class="pa-4 card">
              <v-card-text class="pa-4 card-text">
                <v-list class="pa-0 card-text">
                  <v-list-item
                    class="d-flex justify-start first"
                    color="transparant"
                  >
                    <v-avatar size="30" color="blue" class="pa-0 mx-1">
                      <span class="white--text font-weight-normal font">
                        RS
                      </span>
                    </v-avatar>
                    <div class="texte">
                      <Transition name="fade" mode="out-in">
                        <TextEditor2 />
                      </Transition>
                      
                    </div>
                  </v-list-item>
                </v-list>

                <CommentList />
              </v-card-text>

              <v-card-actions class="d-flex justify-end py-1">
                <v-btn color="primary" text @click="dialog = false"
                  >Close</v-btn
                >
              </v-card-actions>
            </v-card>
          </v-dialog>
        </div>
      </v-card-title>
      <!-- sidebar icon end -->

      <!-- comment dialog -->
      <div>
        <v-dialog v-model="showSingleComment" width="750px">
          <v-card class="pa-2">
            <v-card-text>
              <v-list class="d-flex">
                <v-avatar size="62" class="pt-5" color="black">
                  <v-img
                    src="https://freepngimg.com/thumb/man/22654-6-man-thumb.png"
                  />
                </v-avatar>

                <v-list-item>
                  <v-list-item-content>
                    <v-card-title
                      class="pa-2 rounded-sm text-body-2 font title text-justify"
                    >
                      Lorem ipsum dolor sit amet consectetur adipisicing elit.
                      Sit molestias dolore repudiandae accusantium? Beatae illo
                      ducimus qui, labore dolorum aliquam vitae corporis in
                      dignissimos laborum tenetur natus eligendi possimus nemo
                      alias expedita dolorem magni enim obcaecati consequuntur
                      voluptate. Similique error nesciunt minima dolorum
                      repellat dicta eaque ullam mollitia modi, rem nam harum.
                      Minus eos rem asperiores vero! Incidunt explicabo
                      recusandae obcaecati, id maxime illum provident.
                    </v-card-title>

                    <v-list-item-title class="comment-list">
                      <v-btn
                        @click="showInput = true"
                        icon
                        class="text-body-2 font-weight-normal text-decoration-underline mx-2 py-0 font"
                      >
                        Reply
                      </v-btn>
                      <v-btn
                        @click="showInput = false"
                        icon
                        class="text-body-2 font-weight-normal text-decoration-underline mx-2 py-0 font"
                      >
                        Delete
                      </v-btn>
                      <v-btn
                        @click="showCount = !showCount"
                        icon
                        class="text-body-1 font-weight-normal mx-2 py-0 font"
                      >
                        <v-icon size="18" color="blue"> mdi-paperclip </v-icon>
                      </v-btn>
                      <span class="pt-3 font-weight-bold text-sm">5</span>
                    </v-list-item-title>
                    <div class="comment">
                      <v-avatar size="30">
                        <v-img
                          src="https://freepngimg.com/thumb/man/22654-6-man-thumb.png"
                        />
                      </v-avatar>
                      <v-sheet
                        elevation="0"
                        height="30"
                        width="100%"
                        color="#F8F8F8"
                        class="text-caption font-weight-normal black--text pa-1 pl-3 rounded-lg font"
                      >
                        Lorem ipsum dolor sit amet, consectetur adipisicing
                        elit. Assumenda neque facilis
                      </v-sheet>
                    </div>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-card-text>

            <v-card-actions class="d-flex justify-end py-1">
              <v-btn color="#1D82F5" outlined class="rounded-lg" text
                >Close</v-btn
              >
            </v-card-actions>
          </v-card>
        </v-dialog>
      </div>

      <!-- second dialog -->
      <div>
        <v-dialog v-model="showSingleComment1" width="750px">
          <v-card class="pa-1">
            <v-card-text>
              <v-list class="d-flex">
                <v-avatar size="62" class="pt-5" color="black">
                  <v-img
                    src="https://freepngimg.com/thumb/man/22654-6-man-thumb.png"
                  />
                </v-avatar>

                <v-list-item class="d-block">
                  <v-list-item-content>
                    <v-card-title
                      class="pa-2 rounded-sm text-body-2 font title text-justify"
                    >
                      <textarea v-model="text" class="text-in"></textarea>
                    </v-card-title>

                    <v-list-item-title class="d-flex justify-space-between">
                      <UploadImage />

                      <span class="mt-10">Last update </span>
                    </v-list-item-title>
                  </v-list-item-content>
                </v-list-item>
              </v-list>
            </v-card-text>
          </v-card>
        </v-dialog>
      </div>
    </v-card>
  </div>
</template>

<script>
import CommentList from "../comments/CommentList.vue";
import TextEditor from "../texteditor/TextEditor.vue";
import UploadImage from "../fileupload/UploadImage.vue";
import TextEditor2 from "../texteditor/TextEditor2.vue";

export default {
  data() {
    return {
      show: true,
      showNewInput: false,

      // openText: false,
      currFiles: [],
      readers: [],
      files: [],
      showSingleComment: false,
      showSingleComment1: false,
      addComment: false,
      images: [],
      images1: [],
      text: " Lorem ipsum dolor sit amet consectetur adipisicing elit.Sit molestias dolore repudiandae accusantium? Beatae illo ducimus qui, labore dolorum aliquam vitae corporis in dignissimos laborum tenetur natus eligendi possimus nemo alias expedita dolorem magni enim obcaecati consequuntur voluptate. Similique error nesciunt minima dolorum repellat dicta eaque ullam mollitia modi, rem nam harum.",

      isActive: true,
      dialog: false,
      content2: [
        {
          id: 1,
          name: "Comment",
          title: "Add Comment",
          lists: [
            {
              id: 1,
              text: "this is me",
              icon1: "mdi-eye-outline",
              icon2: "mdi-pencil",
            },
            {
              id: 2,
              text: "this is me",
              icon1: "mdi-eye-outline",
              icon2: "mdi-pencil",
            },
          ],
        },
        {
          id: 2,
          name: "Sub Task",
          title: "Add Sub Task",
          lists: [
            {
              id: 1,
              text: "this is me",
              icon1: "mdi-eye-outline",
              icon2: "mdi-pencil",
            },
            {
              id: 2,
              text: "this is me",
              icon1: "mdi-eye-outline",
              icon2: "mdi-pencil",
            },
          ],
        },
        {
          id: 3,
          name: "Notes",
          title: "Add Notes",
          lists: [
            {
              id: 1,
              text: "this is me",
              icon1: "mdi-eye-outline",
              icon2: "mdi-pencil",
            },
            {
              id: 2,
              text: "this is me",
              icon1: "mdi-eye-outline",
              icon2: "mdi-pencil",
            },
          ],
        },
      ],
    };
  },

  components: {
    CommentList,
    TextEditor,
    UploadImage,
    TextEditor2,
  },

  methods: {
    openText() {
      this.showNewInput = true;
      this.show = false;
    },

    openDialog() {
      this.dialog = true;
      this.isActive = !this.isActive;
    },
    onNewFileUpload() {
      console.log("click");
    },

    addFiles() {
      console.log("files", this.files);
      this.files.forEach((file, f) => {
        this.readers[f] = new FileReader();
        this.readers[f].onloadend = (e) => {
          let fileData = this.readers[f].result;
          let imgRef = this.$refs.file[f];
          imgRef.src = fileData;
          console.log(fileData);
          // send to server here...
        };

        this.readers[f].readAsDataURL(this.files[f]);
      });
    },

    remove(index) {
      this.files.splice(index, 1);
    },
  },
};
</script>

<style scoped>
.texte {
  width: 100%;
}

.comment {
  display: flex;
  justify-content: start;
}

.text-in {
  height: 100px;
  width: 100%;
  padding: 5px;
  border-radius: 5px;
  overflow: hidden;
}

.file {
  height: 60px;
  width: 100%;
}

.v-dialog {
  border: 10px solid gold !important;
}

.card {
  border: 2px solid #1c96e7;
  border-radius: 2%;
  background: #f4f5f7;
}

.card-text {
  background: #f4f5f7;
}

.v-list-item {
  min-height: 30px !important;
}

.title {
  background: #d8d4d447;
  border-radius: 5%;
  padding: 10px;
  letter-spacing: 2px;
}

.v-input__prepend-outer {
  margin-right: 0 !important;
}

.span {
  color: gray;
}

.list-item {
  border-top: 1px solid rgba(128, 128, 128, 0.251);
}

.tagg {
  position: absolute;
  top: 30%;
  left: -10%;
  z-index: 99;
}

.hidden-sm-and-down .v-icon {
  color: white !important;
}

input {
  background: #fff;
  padding: 10px;
  box-shadow: 0 0 2px gray;
  border-radius: 5px;
  font-size: 14px;
  font-weight: 500;
}

.text {
  color: #777777;
  font-size: 14px;
}

.comment-list {
  display: grid;
  grid-template-columns: 60px 60px 40px 30px;
}

.dialog-box {
  display: block !important;
}



.fade-enter-active,
.fade-leave-active {
  transition: all 0.8s ease-in-out;
  opacity: 1;

}

/* .fade-leave-from,
.fade-enter-to{
  transition-delay: 10s;
} */

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: translateX(100%);
  transition: all 0.8s ease-in-out;
}
</style>
