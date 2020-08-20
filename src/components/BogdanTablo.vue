<template>
    <div id = 'root' class = ''     >
        <!-- <div style = 'position: fixed;'>
            {{scrollP}}
        </div> -->
        <div class="rect" :style="{top: 'calc('+scrollPx * 0.4 + 'px + 50%)'} ">{{scrollPx}}</div>
        <div class="rect2" :style="{top: 'calc('+scrollPx * 0.3 + 'px + 10%)'} ">{{scrollPx}}</div>
        <IguanaShape :style="{top: 'calc('+scrollPx * 0.3 + 'px + 10%)'}" />

        <div :style="{marginTop: scrollPx * 0.9 + 'px', position: 'absolute'} " >
            <h1>{{title}}</h1>
        </div>
        <div>

        </div>
    </div>
</template>

<script>
import IguanaShape from "@/components/IguanaShape.vue";

export default {
    name: "BogdanTablo",
    data () {
        return {
            scrollP: 0,
            scrollPx: 0,
            // items: ['a', 'b', 'c']
        }
    },
    components: {
        IguanaShape
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
            this.scrollPx = window.scrollY

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
        width: 100%;
    }
    #root .rect{
        position: absolute;
        height: 2%;
        width: 25%;
        left: 40%;
        background: rgba(255, 125, 19, 0.67)
    }
    #root .rect2{
        position: absolute;
        height: 10%;
        width: 10%;
        left: 10%;
        background: rgba(255, 19, 203, 0.67)
    }
    #root div h1{
        font-weight: 900;
        font-size: 500%;
        float: none;
    }
    #root div p{
        float: none;
    }
</style>
<!-- Add "scoped" attribute to limit CSS to this component only -->
