<template>
    <div>
        <h1>Add Author</h1>

        <form @submit.prevent="addAuthor">

            <input type="text" v-model="author.name" placeholder="type your name">
            <input type="text" v-model="author.phone" placeholder="type your phone">
            <input type="email" v-model="author.email" placeholder="type your email">
            <input type="text" v-model="author.address" placeholder="type your address">

            <button type="submit">Add Author</button>
        </form>

    </div>
</template>


<script>

import gql from 'graphql-tag'

    export default {
        name: 'AuthorsCreate',
        data(){

            return {

                author: {

                    name: '',
                    email: '',
                    phone:'',
                    address:'',
                    country:'',

                }

            }

        },

   methods: {

       addAuthor(){
           this.$apollo.mutate({

               mutation:gql`
               
               mutation {
  
            createAuthor(
                
                name: "${this.author.name}",
                email: "${this.author.email}",
                phone: "${this.author.phone}",
                address: "${this.author.address}",
                country: "${this.author.country}"
                
            ) {
            
                name
                email
                phone
                address
            
        }
    
    
    }

               
               `

           }).then( (data) => {

               console.log(data)
                alert('Author Added')
               this.author = {}
               this.$router.push('/authors')

           }
              
        ).catch((error) => {

            console.log(error)

        })
       }
       
    },

}
</script>