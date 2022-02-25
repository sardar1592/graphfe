<template>

    <div>

        <h1>Authors</h1>

        <ul>

            <li v-for="author in authors.data" :key="author.id">{{author.name}}: {{author.books.length}} Publications</li>

        </ul>

        <nuxt-link to="/authors/create">
        
            <button>Add Author</button>
        
        </nuxt-link>   


    </div>


</template>

<script>
import gql from 'graphql-tag'

export default {
    name: 'Authors',
    apollo: {
        authors: gql`query {
                authors {
                    data {
                        name
                        address
                        email
                        phone, 
                        books {
                            title
                        }
                }
                
            }
                
        }`,
    },
        
}   
</script>