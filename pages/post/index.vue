<template>
    <div>
        <h1>post</h1>
        <post 
        v-for="post of posts"
        :key="post.id"
        :name="post.title"
         :id="post.id"
         />
    </div>
</template>

<script>
import axios from 'axios'
import post from '../../components/post'

export default {
    components:{
        post
    },
    data() {
        return {
            posts: [
            ]
        }
    },
    async created() {
       try {
           const res = await axios.get('https://jsonplaceholder.typicode.com/posts/')
           this.posts = res.data;
       } catch (error) {
            console.log(error)
       }
    }
}

</script>