<template>
  <div>
    <form @submit.prevent="BoodschapToevoegen">
      <input type="text" v-model="title" name="title" placeholder="boodschap toevoegen.."/>
      <input type="submit" value="toevoegen" class="btn"/>
    </form>
  </div>
</template>

<script>
  import { v4 as uuidv4 } from 'uuid';

  export default {
    name: "BoodschapToevoegen",
    data() {
      return {
        title:''
      }
    },
    methods: {
      BoodschapToevoegen() {
        const nieuweBoodschap = {
          id: uuidv4(),
          title: this.title,
          completed: false
        }
        //send up to parent
        this.$emit('boodschap-toevoegen', nieuweBoodschap);

        this.title = '';
      }
    }
  }
</script>


<style scoped>
  form {
    display: flex;
  }
  input[type="text"] {
    flex: 10;
    padding: 5px;
  }
  input[type="submit"] {
    flex: 2;
  }



</style>
