<template>
	<v-container fill-height fluid class="background">
		<v-row>
			<v-col cols="12">
				<v-card class="pa-3" outlined width="600px">
					<v-card-title></v-card-title>
					<v-card-text>
						<v-form>
							<v-text-field v-model="Ime" label="Ime"></v-text-field>
							<v-text-field v-model="Prezime" label="Prezime"></v-text-field>
							<v-text-field v-model="BrojDolazaka" label="Broj dolazaka (maksimalno 15)"></v-text-field>
							<v-text-field v-model="RezultatPrvogKolokvija" label="Rezultat prvog kolokvija (maksimalno 40 bodova)"></v-text-field>
							<v-text-field v-model="RezultatDrugogKolokvija" label="Rezultat drugog kolokvija (maksimalno 40 bodova)"></v-text-field>
							<v-text-field v-model="KontinuiranoPracenje" label="Kontinuirano pracenje (maksimalno 20 bodova)"></v-text-field>
						</v-form>
					</v-card-text>
					<v-card-actions>
						<v-btn
							color="black"
							class="white--text"
							elevation="0"
							@click="obrisiSveUnesenePodatke">
							BRISI PODATKE
						</v-btn>
						<v-spacer></v-spacer>
					</v-card-actions>
				</v-card>
			</v-col>
		</v-row>
	</v-container>
</template>

<script>
export default {
	name: "prvi-zadatak",
	data() {
		return {
			Ime: "",
			Prezime: "",
			BrojDolazaka: "",
			RezultatPrvogKolokvija: "",
			RezultatDrugogKolokvija: "",
			KontinuiranoPracenje: "",
			rules: {
				
			},
		};
	},
	watch: {},
	methods: {
		ocistiFormu() {},
		dodajStudenta() {
			let noviStudent = {
				//Dodaj propertyje
			};
			//ovo ne diraj
			let studenti = JSON.parse(localStorage.getItem("studenti"));
			if (!studenti) {
				studenti = [];
			}
			studenti.push(noviStudent);
			localStorage.setItem("studenti", JSON.stringify(studenti));
		},
		obrisiSveUnesenePodatke() {
			localStorage.clear();
		},
	},
};
</script>
