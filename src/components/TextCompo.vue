<template>
    <div>
      <h1>Hmmm</h1>
      <p>Name</p>
      <input type="text" @change="addname" v-model="name"/><br>      
    </div>
</template>

<script>
export default{
    props:{
       type:{
        posts: Array
       }
    },
    data(){
        return{
            name:''
           // names:this.name
        }
    },
    methods:{
        addname(){
            this.$emit('addnames',this.name)
            console.warn(this.name)
        }

    }
}
</script>