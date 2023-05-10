<script>
import axios from "axios";
 
 export default {
    data() {
        return {
            items: [],
            errors: [],
        };
    },
    // Pulls posts when the component is created.
    created() {
        axios
            .get(`http://localhost:3000`)
            .then((response) => {
            // JSON responses are automatically parsed.
            this.items = response.data;
        })
            .catch((e) => {
            this.errors.push(e);
        });
    },
};


</script>
<template>
    <div class="main">
    <h1>My Recipe Book</h1>
    <button>Add Recipe </button>
    <div class="container" v-for="item in items" :key="item">
        <h2><span>{{item.id}}.</span>{{item.name}} </h2> <h3></h3>
        <h3>{{item.category}} </h3>
        <p>
            {{item.description}}
        </p>
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

h2 {
    font-size: 22px;
    font-family: 'Darker Grotesque', sans-serif;
    color: white;
}

h3 {
    font-size: 18px;
    font-family: 'Darker Grotesque', sans-serif;
    color: #02BD7E;
}



p {
    font-size: 18px;
    font-family: 'Darker Grotesque', sans-serif;
    text-align: justify;
    color: #9F9F9F;
}

span{
    font-size: 25px;
    font-family: 'Darker Grotesque', sans-serif;
    color: #02BD7E;
    text-align: center;
    margin-right: 15px;
}

button {
    width: 100px;
    height: 20px;
    margin: auto;
}

.button-delete {
    width: 40px;
    height: 30px;
    margin: auto;
}
.button-thumbs {
    width: 60px;
    height: 30px;
    margin: auto;
}
.main {
    width : 800px;
    height: auto;
    display: flex;
    flex-direction: column;
    margin: auto;
}

.container {
    margin-bottom: 25px;
}
</style>

