<script setup>
import { ref } from 'vue';
import draggable from 'vuedraggable';
import jsPDF from 'jspdf';
import 'jspdf-autotable';

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

const exportPDF = () => {
  const doc = new jsPDF();
  const date = date();
  const fileName = "Planning"+date+".pdf";
  doc.autoTable({
    head: [['Nom', 'Âge', 'Email']],
    body: items.map(item => [item.name, item.age, item.email])
  });
  doc.save("Planning.pdf");
};

const items = [
  { id: 1, name: 'John Doe', age: 30, email: 'john.doe@example.com' },
  { id: 2, name: 'Jane Doe', age: 25, email: 'jane.doe@example.com' },
  { id: 3, name: 'Bob Smith', age: 40, email: 'bob.smith@example.com' }
];

</script>



<template>
  <h1>Meal Planner</h1>
  <button @click="exportPDF" >Export to PDF</button>
      <table>
      <thead>
        <tr>
          <th>Nom</th>
          <th>Âge</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in items" :key="item.id">
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.email }}</td>
        </tr>
      </tbody>
    </table>
<div class="dashboard">


<table >
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
      <tr>
        <td>Wednesday</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>Thursday</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>Friday</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>Saturday</td>
        <td></td>
        <td></td>
      </tr>
      <tr>
        <td>Sunday</td>
        <td></td>
        <td></td>
      </tr>
    </table>
    

<div class="element-to-convert">
  
    hello,world!
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
  
</div>
</div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Darker+Grotesque:wght@900&display=swap');

h1 {
    font-size: 25px;
    font-family: 'Darker Grotesque', sans-serif;
    color: #02BD7E;
    text-align: center;
}


li {
    list-style: none;
    width: 125px;
    height: 80px;
    background-color: #02BD7E;
    border: solid 1px black;
    color: black;
}

table{ 
    width: 800px;
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

td,th  {
    width: 150px;
    height: 80px;
    border: solid 1px #02BD7E ;

}

.dashboard {
  display: flex;
  align-items: center;
}

.element-to-convert {
  display: flex;
  flex-direction: column;

}

</style>