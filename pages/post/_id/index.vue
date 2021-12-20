<template>
    
    <div class="card">
        <h2> {{post.title}} </h2>
        <p> {{post.id}} </p>
        <p> {{post.body}} </p>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data(){
        return{
            post: {}
        }
    },
    async created() {
        
        const res = await axios.get('https://jsonplaceholder.typicode.com/posts/' + this.$route.params.id)
        this.post = res.data;
    }
}
</script>