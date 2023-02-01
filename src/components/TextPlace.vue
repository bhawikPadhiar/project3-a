<template>
    <div>
        <p>Address</p>
      
        <input type="address" placeholder="address" @change="addaddress" v-model="address"/> 
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
            address:''
           // names:this.name
        }
    },
    methods:{
        addaddress(){
            this.$emit('addaddresses',this.address)
            //console.warn(this.address)
        }

    }
}
</script>