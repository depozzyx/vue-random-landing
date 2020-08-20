<template>
    <div id = 'root' class = 'debug-el'>
        <div class="news-header">
            <h1>{{title}}</h1>
        </div>
    </div>
</template>

<script>
export default {
    name: "BogdanTablo",
    data () {
        return {
            // items: ['a', 'b', 'c']
        }
    },
    props: {
        // data: {
        //     title: '[TITLE]',
        //     desc: '[DESC]',
        //     author: '[AUTHOR]',
        //     rate: '[RATE]',
        //     date: '[DATE]',
        // },
        title: {
			type: String,
			required: true,
			default: '[TITLE]'
		},

        // array: {
        //     type: Array,
        //     required: true,
        //     default: function () { return [] }
        // }
    },
    created: function () {
    },
    methods: {

    }
};
</script>

<style scoped>
    #root{
        float:left;
        width:100%;
        background-color: orange;
    }
</style>
<!-- Add "scoped" attribute to limit CSS to this component only -->
