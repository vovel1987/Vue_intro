<template>
    <li>
        <h2>{{name}}{{ isFavorite ? '(Favorite)' : ''}}</h2>
       
        <button @click="toggleDetails">{{detailsAreVisible ? 'Hide': 'Show'}} Details</button>
        <button @click="toggleFavorite">Favorite</button>
         <button @click="$emit('delete',id)">DELETE</button>
        <ul v-if='detailsAreVisible'>
            <li><strong>Phone:</strong>{{phoneNumber}}</li>
            <li><strong>Email:</strong>{{emailAddress}}</li>
             <li><strong>Id:</strong>{{id}}</li>
        </ul>
    </li>
</template>

<script>
export default {
    // props:[
    //     'name',
    //     'phoneNumber',
    //     'emailAddress',
    //     'isFavorite'
    // ],
    emits:['toggle-favorite','delete'],
    // emits:{
    //     'toggle-favorite': function(id){
    //         if (id) {
    //            return true 
    //         } else {
    //             console.warn('Id is missing!')
    //             return false
    //         }
    //     },
     

    // },
    props:{
        id:{
            type:String,
            required:true
        },
        
        name:{
            type:String,
            required:true
        },
        phoneNumber:{
            type:String,
            required:true
        },
        emailAddress:{
            type:String,
            required:true
        },
        isFavorite:{
            type:Boolean,
            required:true,
            default:false,
            // validator:function(value){
            //   return value === '1' || value === '0'
            // }

        }

    },
    data(){
      return{
         detailsAreVisible:false,
        //  friend:{
        //     id:'manuel',
        //   name:'Manuel',
        //   phone:123456,
        //   email:'manuel@gmail.com'
        //  },
        //  FrIsFavorite:this.isFavorite,

      } 
    },
    methods:{
        toggleDetails(){
            this.detailsAreVisible = !this.detailsAreVisible
        },
        toggleFavorite(){
        //   this.FrIsFavorite =!this.FrIsFavorite
           this.$emit('toggle-favorite',this.id)

        },
      

    }
}
</script>