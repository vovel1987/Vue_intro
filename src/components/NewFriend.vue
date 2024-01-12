<template>
<form @submit.prevent="submitData">
    <div>
        <label for=""> Name</label>
        <input type="text" v-model='enteredName' required>
    </div>
    <div>
        <label for=""> Phone</label>
        <input type="tel" v-model='enteredPhone' required>
    </div>
    <div>
        <label for=""> Email</label>
        <input type="email" v-model='enteredEmail' required>
    </div>
    <button>Add Contact</button>
</form>
    
</template>

<script>
export default {
    emits:['add-contact'],
    data(){
        return {
            enteredName:'',
            enteredPhone:'',
            enteredEmail:''
        }
    },
    methods:{
       submitData(){
         this.$emit('add-contact',this.enteredName,this.enteredPhone,this.enteredEmail)
       }
    }
}
</script>