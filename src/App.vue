<script>
import AppEventList from "./components/AppEventList.vue"

import axios from 'axios'; //importo Axios
import { store } from "./store.js" //state management

export default {
	components: {
		AppEventList
	},
	data() {
		return {
			store
		}
	},
	mounted() {
		this.doThings();

		axios.get("http://127.0.0.1:8000/api/prova").then(risultato => {
			if (risultato.status === 200 && risultato.data.success) {
				console.log(risultato.data.payload);

			} else {

				console.error("Ops... qualcosa è andato storto");
			}
		}).catch(errore => {
			console.error(errore);
		});
	},
	methods: {
		doThings() {
			console.log("App.vue does things");
		}
	}
}
</script>

<template>
	<main>
		<AppComponent />

		<button class="btn btn-primary">
			<font-awesome-icon icon="fa-solid fa-home" class="me-1" />
			<span>Primary button</span>
		</button>
	</main>
</template>

<style lang="scss">
// importo il foglio di stile generale dell'applicazione, non-scoped
@use './styles/general.scss';
</style>

<style scoped lang="scss">
// importo variabili
// @use './styles/partials/variables' as *;

// ...qui eventuale SCSS di App.vue
main {
	padding: 1rem;
}
</style>