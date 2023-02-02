<template>
    <div class="v-select">
        <p>language</p>
        <select class="form-control" @change="addlang" v-model="lang">
            <option disabled value="">please select</option>
            <option>Php</option>
            <option>Javascript</option>
            <option>C#</option>
            <option>C++</option>
        </select>
    </div>
</template>

<script>
export default{
    props:{
        textlangs:{
           type:String,
        default:function(){
            return ''
        }
        }
    },
    data(){
        return{
            lang:this.textlangs
           // names:this.name
        }
    },
    methods:{
        addlang(){
            this.$nextTick(()=>{

                this.$emit('addlangs',this.lang)
               // console.warn(this.lang)
            })
        }

    }
}
</script>