<template>
    <div class="modalbtn">
        <b-button
            class="btn"
            label="Add details from here"
            type="is-primary"
            size="is-medium"
            @click="isComponentModalActive = true" />

        <b-button class="btn">Edit details from here</b-button>

        <b-modal           
            v-model="isComponentModalActive"
            has-modal-card
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
                }
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
</style>
