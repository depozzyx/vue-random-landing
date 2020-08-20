<template>
    <div id = 'root'>

    </div>
</template>

<script>
export default {
    name: "IguanaShape",
    data () {
        return {
            scrollP: 0,
            scrollPx: 0,
            // items: ['a', 'b', 'c']
        }
    },
    props: {
        title: {
			type: String,
			required: true,
			default: '[TITLE]'
		}
    },
};
</script>

<style scoped>
    #root{
        position: absolute;
        height: 10%;
        width: 10% !important;
        left: 10%;
        background: rgba(255, 19, 203, 0.67)
    }
</style>
<!-- Add "scoped" attribute to limit CSS to this component only -->
