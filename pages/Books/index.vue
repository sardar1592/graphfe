<template>
    <div>

        <h1>Books</h1>

        <ul>
            <li v-for="book in books.data" :key="book.id">{{book.title}} with {{book.pages}} pages being sold at ${{book.price}}</li>

        </ul>


    </div>
</template>

<script>

import gql from 'graphql-tag'

export default {

    name: 'Books',
    apollo: {

        books:gql`{

            books {
      
                data {
                
                    title
                    author {
                    name	
                    country
                    }
                    price
                    pages
                    
                
                }
      
    }


        }`


    }

    
}
</script>