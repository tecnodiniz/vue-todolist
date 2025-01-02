<template>

    <div class="input-group mb-3">
        <input v-model="item" @keypress="onKeyPress"  type="text" class="form-control" placeholder="Add item" aria-label="Add item" >
        <button @click="emitItem" class="btn btn-outline-secondary" type="button" id="button-addon2">Add Item</button>
    </div>
   
</template>

<script>
export default {
    data(){
        return{
            item:"",
        }
    },
    methods:{
        emitItem(){
            if(this.item.trim() != ""){
                this.$emit("data-item",this.item);
                this.item = "";
            }
          
        },
        onKeyPress(event){
            if(event.key == "Enter"){
                this.$emit("data-item",this.item);
                this.item = "";
            } 
        }

    }
    
}
</script>
