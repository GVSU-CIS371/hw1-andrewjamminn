<template>
  <div>
    <Beverage 
      :isIced="currentTemp === 'Cold'" 
      :baseClass="currentBase?.id"
      :syrupClass="currentSyrup?.id"
      :creamClass="currentCreamer?.id"
    />
    <ul>
      <li>
        <!--buttons for temps-->
        <template v-for="temp in temps" :key="temp">
          <label>
            <input
              type="radio"
              name="temperature"
              :id="`r${temp}`"
              :value="temp"
              v-model="currentTemp"
            />
            {{ temp }}
          </label>
        </template>
      </li>
      <li>
        <!--buttons for bases-->
        <template v-for="base in bases" :key="base">
          <label>
            <input
              type="radio"
              name="base"
              :id="`r${base}`"
              :value="base"
              v-model="currentBase"
            />
          </label>
          {{ base.name }}
        </template>
      </li>
      <!--buttons for creamer-->
      <li>
        <template v-for="cream in creamers" :key="cream">
          <label>
            <input 
              type="radio"
              name="cream"
              :id="`r${cream}`"
              :value="cream"
              v-model="currentCreamer"
            />
          </label>
          {{ cream.name }}
        </template>
      </li>
      <!--buttons for creamer-->
      <li>
        <template v-for="syrup in syrups" :key="syrup">
          <label>
            <input 
              type="radio"
              name="syrup"
              :id="`r${syrup}`"
              :value="syrup"
              v-model="currentSyrup"
            />
          </label>
          {{ syrup.name }}
        </template>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
import Beverage from "./components/Beverage.vue";
import { temps, bases, creamers, syrups, currentTemp, currentBase, currentCreamer, currentSyrup } from "./stores/beverage";
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
</style>
