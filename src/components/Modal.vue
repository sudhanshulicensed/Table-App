<template>
    <div class="modalbtn">
        {{openModal}}
        <b-button
            class="btn"
            label="Add details from here"
            type="is-primary"
            size="is-medium"
            @click="isComponentModalActive = true" />

        <!-- <b-button @click="isComponentModalActive = true" class="btn">Edit details from here</b-button> -->
        <b-modal    
            class="blur"       
            v-model="isComponentModalActive"
            trap-focus
            :destroy-on-hide="false"
            aria-role="dialog"
            aria-label="Example Modal"
            close-button-aria-label="Close"
            aria-modal>
            <template>
                <AddEditForm :editInput="editInput" :selectedIndex="selectedIndex" :isEdit="isEdit"  :inputData="inputData"/>
            </template>
        </b-modal>
    </div>
</template>

<script>

// import AddEditForm from "add-Edit_Form.vue"
import AddEditForm from "@/components/Add-Edit_Form.vue"

export default {
    name: "FormModal",
    props: {
        inputData: {
            type: Array,
            default: () => [],
        },
        editInput: {
            type: Object,
            default: () => ({}),
        },
        openModal: {
            type: Boolean,
            default: false,
        },
        selectedIndex: {
            type: Function,
            default: null,
        }
    },
    watch: {
        openModal(newVal, oldValue){
            console.log(newVal,oldValue);
            this.isComponentModalActive = newVal;
            this.isEdit = true;
        },
        isComponentModalActive(newVal, oldValue){
            console.log(newVal, oldValue);
            if(!newVal) {
                this.isEdit = false;
            }
        }
    },
    components: {
        AddEditForm,
        },
        data() {
            return {
                isComponentModalActive: false,
                isEdit: false,
            }
        }   
}
</script>

<style scoped>
    .modalbtn{
        display: flex;
        flex-direction: column;
        row-gap: 10px;
    }

    .btn{
        width: 40%;
        margin-left: auto;
        margin-right: auto;
    }

    .blur{
          backdrop-filter: blur(3px);
    }
</style>
