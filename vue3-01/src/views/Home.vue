<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    {{ obj }}
    <button @click="ceshi()"></button>
    <input v-model="obj" />
    <HelloWorld msg="Welcome to Your Vue.js + TypeScript App" />
  </div>
</template>

<script lang="ts">
import { ref, reactive, onMounted, onBeforeMount } from "vue";
// import { Options, Vue, setup } from "vue-class-component";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src

export default ((): any => {
  return {
    name: "Home",
    components: {
      HelloWorld,
    },
    data(): {
      name1: number;
    } {
      return {
        name1: 0,
      };
    },
    beforeMount(): void {
      console.log("beforeMount");
    },
    mounted(): void {
      console.log("mounted");
    },
    beforeCreate(): void {
      console.log("beforeCreate");
    },
    created(): void {
      console.log("created");
    },

    methods: ((): any => {
      return {
        ceshi: function () {
          this;
          console.log("ceshi", this.name1);
          this.name1 = 5;
        },
      };
    })(),
    setup(props: any) {
      let name = ref("小四");
      onBeforeMount(() => {
        console.log("onBeforeMount");
      });
      // onCreate(() => {
      //   console.log("onCreate");
      // });
      // onBeforeCreate(() => {
      //   console.log("onBeforeCreate");
      // });
      onMounted(() => {
        console.log("onMounted");
      });

      const obj = reactive(name);
      console.log(props);

      setTimeout(() => {
        name.value = "56";
      }, 2000);

      return {
        obj,
        // name,
      };
    },
    // setup(function ():any=>{return{ceshi:1}});
    // setup(():any=>{return {}})
    //   setup(props: any) {
    //   const name = ref("小四");
    //   console.log(props);
    //   return {
    //     name,
    //   };
    // }
  };
})();
</script>
