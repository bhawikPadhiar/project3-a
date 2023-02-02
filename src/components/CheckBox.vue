<template>
    <div class="form-control">
        <p>Os</p>   
    <input type="checkbox"  @change="addos" v-model="os" id="windows" value="windows"/>
    <label for="windows" >Windows</label>
    <input type="checkbox" @change="addos" v-model="os" value="Mac"/>
    <label for="mac" >Mac</label>
    <input type="checkbox" @change="addos" v-model="os" value="Linux"/>
    <label for="linux">Linux</label>
    <input type="checkbox" @change="addos" v-model="os" value="centos"/>
    <label for="centos">CentOs</label>
    </div>
</template>

<script>
export default{
    props:{
        textos:{
           type:Array,
        default:function(){
            return []
        }
        }
    },
    data(){
        return{
            os:this.textos
           // names:this.name
        }
    },
    methods:{
        addos(){
            this.$nextTick(()=>{
            this.$emit('addoss',this.os)
          //  console.warn(this.os)
        }) }

    }
}
</script>