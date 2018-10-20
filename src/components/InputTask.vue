<template>
	<div class="new-todo">
		<input class='new-todo' 
		placeholder="O que precisa ser feito?"
		@keyup.enter="addTask" required='required'>
	</div>
</template>

<script type="text/javascript">
	import { Task } from '../models/Task'

	export default {
		data () {
			return {

			}
		},
		methods: {
			addTask ($event) {
				let value = $event.target.value
				let task = new Task()
				task.completed = false
				task.title = value
				console.log(task)
				/* toda instância do Vue (o componente tambem é uma)
				possui o método $emit. Este nos permite emitir um evento
				ele recebe um ou mais argumentos, sendo o primeiro obrigatório
				o restante opicional.

				O primeiro é uma String, que será o nome do evento, os 
				outros são os parametros que você gostaria de enviar junto
				com o seu parametro. em nosso caso queremos avisar o componente
				pai que nós adicionamos a tarefa. */
				this.$emit('newTask', task)
				$event.target.value = ''
			}
		}
	}
</script>

<style type="text/css">
	
</style>
