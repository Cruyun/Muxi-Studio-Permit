<template>
    <input type="text" 
    placeholder="邮箱" 
    ref="input" 
    v-bind:value="value" 
    v-on:input="updateValue($event.target.value)"
    @focus="isFocus" 
    @blur="isBlur">
</template>

<script>
let timeoutId= 1;

export default {
    data() {
            return {}
        },
        props: ['value'],
        created() {
            this.$parent.$parent.email_focus = false
        },
        methods: {
            isFocus() {
                this.$parent.$parent.email_focus = true
            },
            isBlur() {
                this.$parent.$parent.email_focus = false
            },
            updateValue: function(value) {
            	if(timeoutId){
            		clearTimeout(timeoutId)
            		timeoutId = setTimeout(() => {
            			this.$emit('input',value)
            		},2000)
            	}
            }
        }
}
</script>
