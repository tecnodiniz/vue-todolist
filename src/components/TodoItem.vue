<template>
    <div>
        <ul>
            <li v-for="(item, index) in items" :key="index">
                <div class="modal-card d-block" >
                    <div class="modal-dialog">
                        <div class="modal-content bg-primary">
                        <div class="modal-header">
                            <h5 class="modal-title">{{ title }}</h5>
                            <button type="button" class="btn-close"  aria-label="Close" @click="deleteItem(index, category)" ></button>
                        </div>
                        <div class="modal-body">
                            <p>{{ item }}</p>
                        </div>
                        <div class="modal-footer">
                            <!-- <button type="button" class="btn btn-secondary">Close</button> -->
                            <button type="button" class="btn btn-primary" @click="emitIndex(index, category)" >Next</button>
                        </div>
                        </div>
                    </div>
                </div>
               
              
            </li>
           
        </ul>
    </div>
</template>

<script>
export default {
    props:{
        category: Number,
        items: {
            type: Array,
            required: true,
        },
        title: String,
    },
    methods:{
        emitIndex(index, category){
            this.$emit("emit-item", index, category);
        },
        deleteItem(index, category){
            this.$emit("delete-item", index, category);
        }
    }
    
}
</script>
<style>
ul{
    margin: 0;
    padding: 0;
}
ul li{
    list-style: none;
}

.modal-card{
    color: #fff;
    --bs-modal-zindex: 1055;
  --bs-modal-width: 500px;
  --bs-modal-padding: 1rem;
  --bs-modal-margin: 0.5rem;
  --bs-modal-color: ;
  --bs-modal-bg: var(--bs-body-bg);
  --bs-modal-border-color: var(--bs-border-color-translucent);
  --bs-modal-border-width: var(--bs-border-width);
  --bs-modal-border-radius: var(--bs-border-radius-lg);
  --bs-modal-box-shadow: var(--bs-box-shadow-sm);
  --bs-modal-inner-border-radius: calc(var(--bs-border-radius-lg) - (var(--bs-border-width)));
  --bs-modal-header-padding-x: 1rem;
  --bs-modal-header-padding-y: 1rem;
  --bs-modal-header-padding: 1rem 1rem;
  --bs-modal-header-border-color: var(--bs-border-color);
  --bs-modal-header-border-width: var(--bs-border-width);
  --bs-modal-title-line-height: 1.5;
  --bs-modal-footer-gap: 0.5rem;
  --bs-modal-footer-bg: ;
  --bs-modal-footer-border-color: var(--bs-border-color);
  --bs-modal-footer-border-width: var(--bs-border-width);
  z-index: var(--bs-modal-zindex);
  display: none;
  width: 100%;
  height: 100%;
  overflow-x: hidden;
  overflow-y: auto;
  outline: 0;
}
</style>
