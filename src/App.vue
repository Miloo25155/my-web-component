<template>
  <div id="app">
    <div v-if="user" class="col">
      <p v-if="user.name">{{ user.name }}</p>
      <p v-else>No name</p>

      <p v-if="user.age">{{ user.age }}</p>
      <p v-else>No age</p>

      <p v-if="user.mail">{{ user.mail }}</p>
      <p v-else>No mail</p>
    </div>
    <div v-if="!readOnly" class="col" >
      <button v-on:click="edit()" class="btn btn--edit">Edit</button>
      <button v-on:click="remove()" class="btn btn--remove">Remove</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  props:{
    user: {
      type: Object,
      required: true,
      default: function() {
        return {
          name: "Default",
          age: 0,
          mail: "default@mail.com"
        }
      }
    },
    readOnly:{
      type: Boolean,
      default: function(){
        return false
      }
    }
  },
  mounted: function(){
    console.log(this.user);
  },
  methods:{
    edit: function(){
      this.$emit("edit");
    },
    remove: function(){
      this.$emit("remove");
    }
  }
}
</script>

<style scoped>
#app{
  display:flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.col{
  display:flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
}

.btn{
  padding: 5px;
  border-radius: 3px;
  border:none;
  color:white;
}

.btn:hover{
  opacity: 0.7;
}

.btn--edit{
  background-color: #2786c5;
}

.btn--remove{
  background-color: #c52727;
}
</style>
