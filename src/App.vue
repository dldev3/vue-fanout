<template>
  <div
    class="bg-gray-300 text-gray-800 antialiased min-h-screen flex flex-col justify-end"
  >
    <div v-on-clickaway="hideMenu" class="bg-gray-400 p-8 flex justify-center">
      <ul class="absolute -mt-32 space-y-2" style="bottom: 124px">
        <transition v-for="email in emails" :key="email.id" name="fade">
          <li v-show="visible" class="transform" :class="email.classes">
            <a
              href="#"
              class="bg-white hover:bg-gray-100 w-80 shadow-md border rounded-lg p-4 flex items-center"
            >
              <img
                :src="email.image"
                alt="avatar"
                class="rounded-full w-10 h-10"
              />
              <div class="ml-4">
                <div class="font-semibold">{{ email.subject }}</div>
                <div class="text-left text-gray-700">{{ email.sender }}</div>
              </div>
            </a>
          </li>
        </transition>
      </ul>

      <button
        @click="visible = !visible"
        class="bg-white hover:bg-gray-100 w-80 shadow-md border rounded-lg p-4 flex items-center -mt-16"
      >
        <img
          src="https://s3.amazonaws.com/uifaces/faces/twitter/areandacom/128.jpg"
          alt="avatar"
          class="rounded-full w-10 h-10"
        />
        <div class="ml-4">
          <div class="font-semibold">Click Here!</div>
          <div class="text-left text-gray-700">Cards will appear</div>
        </div>
      </button>
    </div>
  </div>
</template>

<script>
import { mixin as clickaway } from "vue-clickaway";

export default {
  mixins: [clickaway],
  name: "App",
  components: {},
  data() {
    return {
      visible: false,
      emails: [
        {
          id: 1,
          subject: "Mechanical Engineer",
          sender: "Jason Freid",
          image: "https://s3.amazonaws.com/uifaces/faces/twitter/enda/128.jpg",
          classes: "translate-x-16 rotate-12",
        },
        {
          id: 2,
          subject: "Lecturer",
          sender: "Michael Doe",
          image:
            "https://s3.amazonaws.com/uifaces/faces/twitter/woodydotmx/128.jpg",
          classes: "translate-x-10 rotate-10",
        },
        {
          id: 3,
          subject: "Software Developer",
          sender: "Jake Walker",
          image:
            "https://s3.amazonaws.com/uifaces/faces/twitter/jeremyshimko/128.jpg",
          classes: "translate-x-6 rotate-8",
        },
        {
          id: 4,
          subject: "Graphic Designer",
          sender: "Coleman Justin",
          image:
            "https://s3.amazonaws.com/uifaces/faces/twitter/_scottburgess/128.jpg",
          classes: "translate-x-4 rotate-6",
        },
        {
          id: 5,
          subject: "Marketing Executive",
          sender: "Zahir Abdhal",
          image:
            "https://s3.amazonaws.com/uifaces/faces/twitter/mattsapii/128.jpg",
          classes: "translate-x-2 rotate-4",
        },
        {
          id: 6,
          subject: "Project Manager",
          sender: "Linda Grace",
          image:
            "https://s3.amazonaws.com/uifaces/faces/twitter/katiemdaly/128.jpg",
          classes: "transform translate-x-1 rotate-2",
        },
      ],
    };
  },
  methods: {
    hideMenu() {
      this.visible = false;
    },
  },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.15s ease-in;
}

.fade-enter,
.fade-laeve-to {
  transform: translate(0px, 100px) rotate(0deg) !important;
  opacity: 0;
}
</style>
