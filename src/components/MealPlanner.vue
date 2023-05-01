<script setup>
import { ref } from 'vue';
import draggable from 'vuedraggable';
const meals = ref([
  'Hamburger',
  'Pizza',
  'Spaghetti',
  'Tacos',
  'Teriyaki Chicken',
]);

const mondayLunch = ref([
]);

const mondayDinner = ref([
]);

const yuckyMeals = ref([
  'Bat wing soup',
  'Spicy Octopus',
  'Anything from Taco Bell',
]);

const columns = ref([
  { header: "Id", name:"id"},
  { header: "Name", name:"name" },
  { header: "Status", name:"status", displayField: "isActive" },
  { header: "Action", name:"action" },
]);

</script>



<template>

<table>
      <tr>
        <th>Day</th>
        <th>Lunch</th>
        <th>Dinner</th>
      </tr>
      <tr>
        <td>Monday</td>
        <td>
          <draggable v-model="mondayLunch" tag="ul" group="meals">
            <template #item="{ element: meal }">
              <li>{{ meal }}</li>
            </template>
          </draggable>
         </td>
        <td><draggable v-model="mondayDinner" tag="ul" group="meals">
      <template #item="{ element: meal }">
      <li>{{ meal }}</li>
    </template>
  </draggable>
  </td>
      </tr>
      <tr>
        <td>Tuesday</td>
        <td></td>
        <td></td>
      </tr>
    </table>
    hello,world!
  <h1>Lundi</h1>
  <h1>Lundi lunch</h1>
  <draggable v-model="mondayLunch" tag="ul" group="meals">
    <template #item="{ element: meal }">
      <li>{{ meal }}</li>
    </template>
  </draggable>
  <h1>Lundi dinner</h1>
  <draggable v-model="mondayDinner" tag="ul" group="meals">
    <template #item="{ element: meal }">
      <li>{{ meal }}</li>
    </template>
  </draggable>
  <h1>Favorite Foods</h1>

  <draggable v-model="meals" tag="ul" group="meals">
    <template #item="{ element: meal }">
      <li>{{ meal }}</li>
    </template>
  </draggable>

  <h1>Terrible Foods</h1>
  <draggable v-model="yuckyMeals" tag="ul" group="meals">
    <template #item="{ element: meal }">
      <li>{{ meal }}</li>
    </template>
  </draggable>
</template>

<style scoped>

li {
    list-style: none;
    width: 125px;
    height: 80px;
    background-color: #02BD7E;
    border: solid 1px black;
    color: black;
}

table{ 
    width: 400px;
    height: 150px;
    margin: auto;
    text-align: center;
    border: solid 1px #02BD7E ;
}

tr
 {
    width: 150px;
    height: 80px;
    border: solid 1px #02BD7E ;

}

td {
    width: 150px;
    height: 80px;
    border: solid 1px #02BD7E ;

}

</style>