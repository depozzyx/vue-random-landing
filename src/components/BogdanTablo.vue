<template>
    <div id = 'root' class = ''     >
        <!-- <div style = 'position: fixed;'>
            {{scrollP}}
        </div> -->
        <div class="rect"></div>
        <div class = 'debug-el' :style="{marginTop: scrollP - 52 + '% !important', position: 'fixed'} " >
            <h1>{{title}}</h1>
        </div>
        <div>

        </div>
    </div>
</template>

<script>
export default {
    name: "BogdanTablo",
    data () {
        return {
            scrollP: '100% !important',
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
        isPlaceholder: {
			type: Boolean,
			required: true,
			default: false
		},
        isFixed: Boolean,

        // array: {
        //     type: Array,
        //     required: true,
        //     default: function () { return [] }
        // }
    },
    created: function () {
        window.addEventListener('scroll', this.handleScroll);
    },
    methods: {
        handleScroll() {
            let d = this.$el.clientHeight - window.scrollY
            let m = d / (window.innerHeight / 100)
            // console.log(m)
            // if (Math.round(m) == 10){
            //     this.scrollP = '100% !important'
            // }
            if (m < 5){
                if (this.scrollP != 5){
                    this.scrollP = 5
                }
            }else{
                this.scrollP = m
            }

        }
    }
};
</script>

<style scoped>
    #root{
        float:left;
        width:100%;
        font-family: 'Montserrat', sans-serif;
    }
    #root div{
        display: flex;
        justify-content: center;
        align-items: center;
        background: #fff;
        width: 100%;
    }
    #root .rect{
        position: absolute;
        top: 5%;
        height: 10%;
        width: 25%;
        left: 5%;
        background: red;
    }
    #root div h1{
        font-weight: 900;
        font-size: 500%;
    }
</style>
<!-- Add "scoped" attribute to limit CSS to this component only -->
