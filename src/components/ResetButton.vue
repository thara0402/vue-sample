<template>
    <b-button type="is-success" @click="onClick">
        <slot></slot>
    </b-button>
</template>

<script lang="ts">
    import {Component, Emit, Prop, Vue} from "vue-property-decorator";

    @Component
    export default class ResetButton extends Vue{
        private initialValue!: string;
 
        @Prop()
        public value!: string;

        @Emit()
        public input(value: string){

        }

        public created(){
            this.initialValue = this.value;
        }

        public onClick(){
            this.input(this.initialValue);
        }
        
    }
</script>

