<template>
	<v-container fill-height fluid class="background">
		<v-row>
			<v-col cols="12">
				<v-card class="pa-3" outlined width="600px">
					<v-card-title></v-card-title>
					<v-card-text>
						<v-form v-model="isFormValid">
							<v-text-field v-model="Ime" label="Ime" :rules="[rules.requiredIme, rules.ispravnoIme]"></v-text-field>
							<v-text-field v-model="Prezime" label="Prezime" :rules="[rules.requiredPrezime, rules.ispravnoPrezime]"></v-text-field>
							<v-text-field v-model="BrojDolazaka" label="Broj dolazaka (maksimalno 15)" :rules="[rules.requiredBrojDolazaka, rules.ispravnoBrDolazaka]"></v-text-field>
							<v-text-field v-model="RezultatPrvogKolokvija" label="Rezultat prvog kolokvija (maksimalno 40 bodova)" :rules="[rules.requiredRezultatPrvogKolokvija, rules.ispravnoR1]"></v-text-field>
							<v-text-field v-model="RezultatDrugogKolokvija" label="Rezultat drugog kolokvija (maksimalno 40 bodova)" :rules="[rules.requiredRezultatDrugogKolokvija, rules.ispravnoR2]"></v-text-field>
							<v-text-field v-model="KontinuiranoPracenje" label="Kontinuirano pracenje (maksimalno 20 bodova)" :rules="[rules.requiredKontinuiranoPracenje, rules.ispravnoKP]"></v-text-field>
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
						<v-spacer></v-spacer>
						<v-spacer></v-spacer>
						<v-btn class="ma-2" outlined color="red" @click="ocisti" :disabled="!isFormValid">OCISTI</v-btn>
						<v-btn :disabled="!isFormValid">OK</v-btn>
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
				requiredIme: value => !!value || 'Required.',
				requiredPrezime: value => !!value || 'Required.',
				requiredBrojDolazaka: value => !!value || 'Required.',
				requiredRezultatPrvogKolokvija: value => !!value || 'Required.',
				requiredRezultatDrugogKolokvija: value => !!value || 'Required.',
				requiredKontinuiranoPracenje: value => !!value || 'Required.',
				ispravnoIme: value => value.length > 3 || "Mora biti vise od 3 znaka",
				ispravnoPrezime: value => value.length > 3 || "Mora biti vise od 3 znaka",
				ispravnoBrDolazaka: value => value > 11 && value < 16 || "Broj dolazaka mora biti veći od 11",
				ispravnoR1: value => value > 20 && value < 41 || "Bodovi moraju prelaziti 50%",
				ispravnoR2: value => value > 20 && value < 41 || "Bodovi moraju prelaziti 50%",
				ispravnoKP: value => value > 5 && value < 21|| "Broj bodova mora biti veći od 5"
			},
			isFormValid: false,
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
		ocisti () {
        	this.Ime = "";
			this.Prezime = "";
			this.BrojDolazaka = "";
			this.RezultatPrvogKolokvija = "";
			this.RezultatDrugogKolokvija = "";
			this.KontinuiranoPracenje = "";
      	},
	},
};
</script>
