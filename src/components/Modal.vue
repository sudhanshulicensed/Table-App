<template>
    <div class="modalbtn">
        <b-button
            class="btn"
            label="Add details from here"
            type="is-primary"
            size="is-medium"
            
            @click="isComponentModalActive = true" />

        <b-button @click="isComponentModalActive = true">Edit details from here</b-button>

        <b-modal           
            v-model="isComponentModalActive"
            trap-focus
            :destroy-on-hide="false"
            aria-role="dialog"
            aria-label="Example Modal"
            close-button-aria-label="Close"
            aria-modal>
            <template>
                <AddEditForm :inputData="inputData"/>
            </template>
        </b-modal>
    </div>
</template>

<script>

import AddEditForm from "./Add-Edit_Form.vue"

export default {
    name: "FormModal",
    props: {
        inputData: {
            type: Array,
            default: () => [],
        }
    },
    components: {
        AddEditForm,
        },
        data() {
            return {
                isComponentModalActive: false,
                formProps: {
                    email: 'evan@you.com',
                    password: 'testing',
                },
                overlay: false,
            }
    },
    methods: {
        // showOverlay() {
        //     this.overlay= true;
        // }
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
    
    /* .overlay{
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.7);
        backdrop-filter: blur(3px);
        z-index: 5;
    } */
</style>
