<template>
	<div id = 'root'>
		<BogdanTablo title = 'Bogdan.Info' isFixed/>
		<!-- <BogdanTablo title = 'Bogdan.Info' isPlaceholder /> -->
		<OlegDiv title = 'Bogdan.Info'/>
		<OlegDiv title = 'Bogdan.Info'/>
	</div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import BogdanTablo from "@/components/BogdanTablo.vue";
import OlegDiv from "@/components/OlegDiv.vue";

function getCookie(name) {
	const value = `; ${document.cookie}`;
	const parts = value.split(`; ${name}=`);
	if (parts.length === 2) return parts.pop().split(';').shift();
}

export default {
	name: "Home",
	components: {
		BogdanTablo,
		OlegDiv
		// md-display-3
		// HelloWorld,
		// Bogdan
	},
	created(){
		let c1 = getCookie('todoNames')
		let c2 = getCookie('todoState')
		if (c1){
			console.log(c1)
			console.log(c2)
			let a = c1.split('//')
			let b = c2.split('//')
			for (let i = 0; i < a.length; i++) {
				this.todoTitles.push(a[i])
				this.todoStates.push(parseInt(b[i]))
			}
			for (let i = 0; i < this.todoStates.length; i++) {
				if (this.todoStates[i] == 1){
					this.todoChecked.push(i)
				}
			}
        }

	},
	data: () => ({
		notification: [],
		todoChecked: [],
		hasMessages: false,
		todoText: '',
		todoTitles: [],
		todoStates: [],
		// todoList: [['Todo',0], ['Todo2',1]],
	}),
    computed: {
      messageClass () {
        return {
          'md-invalid': this.hasMessages
        }
      }
	},
	methods: {
		addTodo() {
            if (this.checkError()){
				this.todoTitles.unshift(this.todoText);
				this.todoStates.unshift(0);
				this.todoText = ''
				for (let i = 0; i < this.todoChecked.length; i++) {
					this.todoChecked[i] += 1
					this.updateTodoClicked()
				}

				let a = this.todoTitles.join('//')
				let b = this.todoStates.join('//')
				document.cookie = `todoNames=${a};`
				document.cookie = `todoState=${b};`
				console.log(document.cookie, getCookie('todoNames'))
			}
		},
		checkError() {
			if (this.todoText == ''){
				this.hasMessages = true
				return 0
			}else{
				this.hasMessages = false
				return 1
			}
		},
		updateTodoClicked(){
			for (let i = 0; i < this.todoStates.length; i++) {
				let f = 0
				for (let m = 0; m < this.todoChecked.length; m++) {
					if (this.todoChecked[m] == i){
						this.todoStates[i] = 1
						f = 1
						break
					}
				}
				if (f == 0){
					this.todoStates[i] = 0
				}
				let b = this.todoStates.join('//')
				document.cookie = `todoState=${b};`
			}
		}
	}
};
</script>

<style scoped>
	.home{
		height: 100%;
	}
	#root{
		height: 100%;
	}
	md-layout-item{
		height: 100%;
	}
</style>
