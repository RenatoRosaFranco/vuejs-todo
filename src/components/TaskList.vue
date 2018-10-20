<template>
	<ul class="todo-list">
		<li v-for="(todo, index) in sortedTasks" class='todo' :key='index'>
			<div class="view">
				<input @click="completeTask(todo)" class='toggle' type='checkbox'>
				<label v-bind:class="{ 'todo-completed': todo.completed }">
				{{ todo.title }}</label>
			</div>
		</li>
		<div v-show="todoList == 0">
			None task registered yet
		</div>
	</ul>
</template>

<script type="text/javascript">
	export default {
		/* props evidencia que o componente pai passara
		atributos para o componente filho, props define
		quais são esses atributos. */ 
		props: ['todoList'],
		/* Propriedades computadas são como funções, porem ela é 
		usada apenas para devolver um valor, sem alterar o estado
		original do componente */

		/*
			v-if = renderiza ou não o componente/dado.
			v-show = aplica o estilo display:none dependendo do resultado
			ou seja, o elemento existe, mas está escondido.
		*/
		computed: {
			sortedTasks: function(){
				let sorted = this.todoList.slice()
				return sorted.sort(function(a, b) {
					if ( a.title < b.title ) return -1
					if ( a.title > b.title ) return 1
					return 0;
				})
			}
		},
		methods: {
			completeTask (task) {
				task.completed = !task.completed
			}
		}
	}
</script>

<style type="text/css">
	.todo-completed {
		text-decoration: line-through;
	}
</style>