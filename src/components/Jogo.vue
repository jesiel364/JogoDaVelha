<template>
  <div class="container">
    <strong v-if="empate">EMPATE</strong>
    <div class="tabuleiro_card">
      <div @click="jogada(pos)" v-for="(pos, key) in celulas" class="celula">
        <v-btn
          id="pos.pos"
          v-if="pos.on && pos.player === 'x'"
          class="bg-brown"
          theme="dark"
          size="x-large"
          icon="mdi-alpha-x"
        ></v-btn>
        <v-btn
          id="pos.pos"
          v-if="pos.on && pos.player === 'o'"
          theme="dark"
          size="x-large"
          icon="mdi-alpha-o"
        ></v-btn>
      </div>
    </div>

    <div class="desc">
      <div>
        <p v-for="item in jogadas">
          <span v-if="item.player == 'x'"
            ><strong>Jogador X:</strong> {{ item.pos }}</span
          >

          <span v-else="item.player == 'o'"
            ><strong>Jogador O:</strong> {{ item.pos }}</span
          >

          <!--<span><strong>pos:</strong> {{ item.pos }}</span>-->
        </p>
      </div>

      <div>
        <p>
          <span><strong>Ultima jogada:</strong> {{ ultimaJogada.player }}</span
          ><br />
          <span><strong>Pos.:</strong> {{ ultimaJogada.pos }}</span>
        </p>
        <v-btn @click="reiniciar()">Reiniciar</v-btn>
      </div>
    </div>
  </div>
</template>

<style>
.tabuleiro_card {
  background-color: #282828;
  max-width: 100%;
  height: auto;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-template-rows: 100px 100px 100px;
  padding: 5px;
  border-radius: 8px;
  align-content: center;
  margin: 0 auto;
  
}

.celula {
  background-color: #363636;
  margin: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  width: auto;
}

.desc {
  display: flex;
  width: auto;
  justify-content: space-between;
  /*background-color: blue;*/
}
</style>

<script>
export default {
  props: ["message"],
  data() {
    return {
      celulas: [
        { pos: 1, on: false, player: "" },
        { pos: 2, on: false, player: "" },
        { pos: 3, on: false, player: "" },

        { pos: 4, on: false, player: "" },
        { pos: 5, on: false, player: "" },
        { pos: 6, on: false, player: "" },

        { pos: 7, on: false, player: "" },
        { pos: 8, on: false, player: "" },
        { pos: 9, on: false, player: "" },
      ],
      jogadas: [],
      ultimaJogada: [],
      total: "",
      empate: false,
    };
  },

  methods: {
    verificar() {
      
      const jogadas = this.jogadas;
      const ultimaJogada = this.ultimaJogada;

      let row_1x = [];
      let row_2x = [];
      let row_3x = [];
      let col_1x = [];
      let col_2x = [];
      let col_3x = [];
      let diag_1x = [];
      let diag_2x = [];
      let row_1o = [];
      let row_2o = [];
      let row_3o = [];
      let col_1o = [];
      let col_2o = [];
      let col_3o = [];
      let diag_1o = [];
      let diag_2o = [];

      for (let chave in jogadas) {
        if (jogadas[chave].player === "x") {
          // linha 1
          if (
            jogadas[chave].pos === 1 ||
            jogadas[chave].pos === 2 ||
            jogadas[chave].pos === 3
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            row_1x.push([pos, player]);
          }

          // linha 2
          if (
            jogadas[chave].pos === 4 ||
            jogadas[chave].pos === 5 ||
            jogadas[chave].pos === 6
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            row_2x.push([pos, player]);
          }

          // linha 3
          if (
            jogadas[chave].pos === 7 ||
            jogadas[chave].pos === 8 ||
            jogadas[chave].pos === 9
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            row_3x.push([pos, player]);
          }

          // coluna 1
          if (
            jogadas[chave].pos === 1 ||
            jogadas[chave].pos === 4 ||
            jogadas[chave].pos === 7
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            col_1x.push([pos, player]);
          }

          // coluna 2
          if (
            jogadas[chave].pos === 2 ||
            jogadas[chave].pos === 5 ||
            jogadas[chave].pos === 8
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            col_2x.push([pos, player]);
          }

          // coluna 3
          if (
            jogadas[chave].pos === 3 ||
            jogadas[chave].pos === 6 ||
            jogadas[chave].pos === 9
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            col_3x.push([pos, player]);
          }

          // diagonal 1
          if (
            jogadas[chave].pos === 1 ||
            jogadas[chave].pos === 5 ||
            jogadas[chave].pos === 9
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            diag_1x.push([pos, player]);
          }

          // diagonal 2
          if (
            jogadas[chave].pos === 3 ||
            jogadas[chave].pos === 5 ||
            jogadas[chave].pos === 7
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            diag_2x.push([pos, player]);
          }
        } else {
          // linha 1
          if (
            jogadas[chave].pos === 1 ||
            jogadas[chave].pos === 2 ||
            jogadas[chave].pos === 3
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            row_1o.push([pos, player]);
          }

          // linha 2
          if (
            jogadas[chave].pos === 4 ||
            jogadas[chave].pos === 5 ||
            jogadas[chave].pos === 6
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            row_2o.push([pos, player]);
          }

          // linha 3
          if (
            jogadas[chave].pos === 7 ||
            jogadas[chave].pos === 8 ||
            jogadas[chave].pos === 9
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            row_3o.push([pos, player]);
          }

          // coluna 1
          if (
            jogadas[chave].pos === 1 ||
            jogadas[chave].pos === 4 ||
            jogadas[chave].pos === 7
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            col_1o.push([pos, player]);
          }

          // coluna 2
          if (
            jogadas[chave].pos === 2 ||
            jogadas[chave].pos === 5 ||
            jogadas[chave].pos === 8
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            col_2o.push([pos, player]);
          }

          // coluna 3
          if (
            jogadas[chave].pos === 3 ||
            jogadas[chave].pos === 6 ||
            jogadas[chave].pos === 9
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            col_3o.push([pos, player]);
          }

          // diagonal 1
          if (
            jogadas[chave].pos === 1 ||
            jogadas[chave].pos === 5 ||
            jogadas[chave].pos === 9
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            diag_1o.push([pos, player]);
          }

          // diagonal 2
          if (
            jogadas[chave].pos === 3 ||
            jogadas[chave].pos === 5 ||
            jogadas[chave].pos === 7
          ) {
            let pos = jogadas[chave].pos;
            let player = jogadas[chave].player;
            diag_2o.push([pos, player]);
          }
        }
      }

      let matchs = [
        row_1x,
        row_2x,
        row_3x,
        col_1x,
        col_2x,
        col_3x,
        diag_1x,
        diag_2x,
        row_1o,
        row_2o,
        row_3o,
        diag_1o,
        diag_2o,
      ];

      let trio = [];

      for (let index in matchs) {
        if (matchs[index].length === 3) {
          if (matchs[index][0][1] === "x") {
            alert("Vitória do X");
          } else {
            alert("Vitória do O");
          }
        }

        if (matchs[index].length == 3) {
          trio.push(matchs[index]);
          
        }
      }
      
      let yes = []
     
      if (trio.length < 3) {
        let celulas = this.celulas
        for(let chave in celulas){
          if(celulas[chave].on == true){
            yes.push(celulas[chave])
            
        }
      }
      }
      if (yes.length == 9){
        
        if(trio == 0){
          alert('EMPATE')
          this.empate = true
        }
        
      }
      
    },

    jogada(pos) {
      
      if (this.ultimaJogada.player == "x") {
        
        if (pos.on == false) {
          pos.on = true;
          pos.player = "o";
          this.jogadas.push(pos);
          this.ultimaJogada = pos;
          this.verificar()
          // alert(`cond1 ${pos.player}, ${pos.pos}`)
        } else {
          alert("A célula já foi marcada");
        }
      } else {
        
        if (pos.on == false) {
          pos.on = true;
          pos.player = "x";
          this.jogadas.push(pos);
          this.ultimaJogada = pos;
          this.verificar()
          //alert(`cond2 ${pos.player}, ${pos.pos}`)
        } else {
          alert("A célula já foi marcada");
        }
      }
      
    },
    
    reiniciar() {
      isso
      alert(this.celulas)
      
      // celulas = this.celulas
      // for(let chave in celulas){
      //   alert(this.celulas[chave].on)
      //   this.celulas[chave].player = ''
      // }
    },
    
  },
};
</script>
