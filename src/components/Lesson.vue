<script>
export default {
    props:['sortedLessons'],
    methods:{
        addToCart(lesson){
            this.$emit('addToCart',lesson)
        }
    }
}
</script>

<template>
         <div v-for="(lessons, index) in sortedLessons" :key="`lesson--${index}`" class="lessons__item col-md-3 py-2">
                        <img class="card-img-top" v-bind:src="lessons.image" width="200" height="250" >
                        <div class="card-body">       
                        
                            
                            <h2 class="card-title"><p>Subject: {{ lessons.title }}</p></h2>
                            
                            <p class="card-text">Location: {{ lessons.location }}</p>
                            <p class="card-text">Price: {{ lessons.price }}</p>
                            <div>
                            
                            <p class="card-text">Spaces: {{lessons.availableInventory}}</p>
                            <button class="btn btn-dark" v-on:click='addToCart(lessons)' :disabled="!lessons.availableInventory">Add to
                                cart</button>
                            <span v-if="lessons.availableInventory">{{'Left '+ lessons.availableInventory}}</span>
                            <span v-else>This lesson is fully booked!</span>
                        </div>
                    </div>
                    </div>

</template>