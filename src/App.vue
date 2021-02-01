<template>
  <div>
    <!-- <h1>{{ count }}</h1>
    <h1>{{ double }}</h1> -->
    <!-- <ul>
      <li v-for="number in numbers" :key="number">
        <h1>{{ number }}</h1>
      </li>
    </ul>
    <h1>{{ person.name }}</h1>
    <button @click="increase">+1</button> -->
    <div>{{ x }}</div>
    <div>{{ y }}</div>

    <modal />
  </div>
</template>

<script lang="ts">
import useMousePosition from "./hooks/useMousePosition";
import useURLLoader from "./hooks/useURLLoader";
import modal from "./components/modal.vue";

import {
  ref,
  computed,
  reactive,
  toRefs,
  onMounted,
  onUpdated,
  onRenderTriggered,
  watch,
  toRef,
  onUnmounted,
} from "vue";

interface DataProps {
  count: number;
  double: number;
  numbers: number[];
  person: { name?: string };
}

interface DogMessage {
  mesage: string;
  status: number;
}

interface CatResult {
  id: string;
  url: string;
  width: number;
  height: number;
}

export default {
  name: "App",
  components: {
    modal
  },
  setup() {
    const data: DataProps = reactive({
      count: 0,
      double: 0,
      numbers: [0, 1, 2],
      person: {},
    });

    const greetings = ref("");
    const updateGreeting = () => {
      greetings.value += "Hello!";
    };

    watch([greetings, () => data.count], (newValue, oldValue) => {
      document.title = "updated" + greetings.value + data.count;
    });

    data.numbers[0] = 5;

    data.person.name = "viking";

    const refData = toRefs(data);

    // const x = ref(0);
    // const y = ref(0);

    // const updateMouse = (e: MouseEvent) => {
    //   x.value = e.pageX;
    //   y.value = e.pageY;
    // };

    // onMounted(() => {
    //   document.addEventListener("click", updateMouse);
    // });

    // onUnmounted(() => {
    //   document.removeEventListener('click', updateMouse);
    // });

    const { x, y } = useMousePosition();

    const { result, loading, loaded } = useURLLoader<CatResult[]>(
      "http://xxx.com"
    );

    watch(result, () => {
      if (result.value) {
        console.log("value", result.value[0].url);
      }
    });

    return {
      ...refData,
      x,
      y,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
