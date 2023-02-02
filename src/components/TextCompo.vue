<template>
    <div>

        <p>Name</p>
        <input class="form-control"  type="text"  @change="addname" v-model="name" /><br>
      
    </div>
</template>

<script>
export default {
    props: {
        textdata:{
           type:String,
            default:''
        }
    },
  
    data() {
        return {
            name:this.textdata
          
            // names:this.name
        }
    },
    methods: {
        addname() {
            this.$emit('addnames', this.name)
             // console.warn(this.name)
        }

    }
}
</script>