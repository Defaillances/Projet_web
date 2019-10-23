<template>
  <v-container>
    <div v-show="Accueil"> 
      Bienvenu sur Choupy, le jeu pour améliorer votre vocabulaire, 
      vous allez devoir trouver des mots à partir de la définition qu'on vous donne, 
      du nombre de lettres et du type (nom, adjectif ...). Vous aurez le droit à 2 erreurs,
      quand vous vous trompez 2 fois sur le même mot, nous vous donnons la première lettre du mot en indice.
      Bonne chance ! 
    <p><v-btn @click="Page_Accueil"> Jouer </v-btn></p>
    </div>
    <div v-show ="!Accueil">
    <p>La définition du mot est : {{Mots[n].def}}</p>
    <p v-show="montrer_indice">La première du mot est : {{Mots[n].indice}}</p>
    <p>Le mot est un : {{Mots[n].type}}</p>
    <p>Le mot est composé de {{Mots[n].nbLettre}} lettres</p>
    <v-btn @click="indentation">mot suivant</v-btn>
    <v-text-field v-model="reponse" label="Entrez votre réponse">Entrez votre réponse</v-text-field>
    </div>
  </v-container>
</template>

<script>

export default {
  data: () => ({
    Mots: [
      {
        mot: 'tonitruant',
        type: 'Adjectif',
        nbLettre: 10,
        def: 'Bruit de tonnerre, bruit énorme',
        indice: 'T',
      },
      {
        mot: 'absurde',
        type: 'Adjectif et nom masculin',
        nbLettre: 7,
        def: 'Contre raison, contre logique',
        indice: 'A',
      },
      {
        mot: 'sébum',
        type: 'Nom masculin',
        nbLettre: 5,
        def: 'Sécrétion grasse produite par les glandes sébacées (la peau)',
        indice: 'S',
      },
      {
        mot: 'iridescent',
        type: 'Adjectif',
        nbLettre: 10,
        def: 'Qui a des reflets colorés de manière changeante',
        indice: 'I',
      },
      {
        mot: 'convexe',
        type: 'Adjectif',
        nbLettre: 7,
        def: "Courbé, arrondi vers l'éxterieur",
        indice: 'C',
      },
      {
        mot: 'concave',
        type:'Adjectif',
        nbLettre: 7,
        def: "Courbé, arrondi vers l'intérieur",
        indice: 'C',
      },
      {
        mot: 'anosognosie',
        type:'Nom féminin',
        nbLettre: 11,
        def: "Trouble neuropsychique qui fait qu'un patient atteint d'une maladie ne semble pas avoir conscience de sa condition",
        indice: 'A',
      },
      {
        mot: 'effervescence',
        type: 'Nom féminin',
        nbLettre: 13,
        def: "Bouillonnement d'un liquide par un dégagement de gaz. Peut également désigner une vive agitation",
        indice: 'E',
      },
      {
        mot: 'transcendant',
        type: 'Adjectif',
        nbLettre: 12,
        def: "Qui s'élève au-dessus du niveau moyen",
        indice: 'T',
      },
      {
        mot: 'trivial',
        type: 'Adjectif',
        nbLettre: 7,
        def: 'Ordinaire, commun',
        indice: 'T',
      },
      {
        mot: 'ordinal',
        type: 'Adjectif',
        nbLettre: 7,
        def: 'qui désigne un rang',
        indice: 'O'
      },
      {
        mot: 'ascension',
        type: 'Nom',
        nbLettre: 8,
        def: 'Elevation, action de gravir',
        indice: 'A'
      },
      {
        mot: 'eveil',
        type: 'Nom',
        nbLettre: 5,
        def: "Tirer quelqu'un de son sommeil, rendre quelque chose effectif",
        indice: 'E',
      },
      {
        mot: 'draconien',
        type:'Adjectif',
        nbLettre: 9,
        def: 'sévérité extrême',
        indice: 'D',
      }

    ],
    n: 0,
    reponse: '',
    i: 0,
    Accueil: true,
    Jeux: false,
    montrer_indice: false
  }),
  methods: {

    Page_Accueil (){
      this.Accueil = false
    },

    indentation () {
      if (this.reponse === this.Mots[this.n].mot) {
        this.n = this.n +1;
      } else {
        this.i = this.i + 1;
        if (this.i == 2) {
          this.montrer_indice = true
        }
        }
      console.log(this.i),
      console.log(this.n),
      console.log(this.reponse);
    return ''
    }
  }
};
</script>
