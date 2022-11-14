<template>
  <div class="cadastro_ingressante">
    <div class="card">
      <div class="title">Cadastro de Ingresantes</div>
      <div class="form">
        <a>Nome</a>     
          <input type="text" class="input" />

          <label id="course">Curso</label> 
          <select for="course" v-model="curso" class="classic">
            <option v-for="curso in cursos" :key="curso.cursoName" :value="curso.cursoName">
              {{ curso.cursoName }}
            </option>
          </select>   
          
          <label id="state">Estado</label> 
          <select for="state" @change="switchSelect($event)" v-model="estado" class="classic">
            <option v-for="estado in estados" :key="estado.estadoName" :value="estado.estadoName" >
              {{ estado.estadoName }}
            </option>
          </select>

          <label id="city">Cidade</label> 
          <select for="city" v-model="municipio" class="classic">
            <option v-for="cidade in cidadesEscolhidas" :key="cidade.cidadeName" :value="cidade.cidadeName">
              {{ cidade.cidadeName }}
            </option>
          </select>
          
          <div class="button">
            <button class="voltar">Voltar</button>
            <button class="gravar">Gravar</button>
          </div>

      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      selected: "",
      municipio:"",
      cidadesEscolhidas:"",
      cursos: [{"cursoName":"Matemática"}, {"cursoName":"Letras"}, {"cursoName":"Geografia"}],
      estados: [{"estadoName":"São Paulo"}, {"estadoName":"Rio de Janeiro"}, {"estadoName":"Minas Gerais"}],
      cidades: {
        cidadeSP: [{"cidadeName":"Mogi das Cruzes"}, {"cidadeName":"Suzano"}, {"cidadeName":"Poá"}, {"cidadeName":"Guararema"}],
        cidadeRJ: [{"cidadeName":"Angra dos Reis"}, {"cidadeName":"Niterói"}, {"cidadeName":"Itaboraí"}],
        cidadeMG: [{"cidadeName":"Belo Horizonte"}, {"cidadeName":"Monte Azul"}, {"cidadeName":"Muzambinho"}],
      }
    };
  },

  methods: {
    switchSelect(event) {
      this.selected = event.target.value;
      console.log(this.cidades)
       if(this.selected =="São Paulo"){
          this.cidadesEscolhidas = this.cidades.cidadeSP
        }else if(this.selected =="Rio de Janeiro"){
          this.cidadesEscolhidas = this.cidades.cidadeRJ
        }else if(this.selected =="Minas Gerais"){
         this.cidadesEscolhidas = this.cidades.cidadeMG
        }
      }  
    }  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.form {
  display: flex;
  flex-direction: column;
  text-align: left;
  max-width: 200px;
  margin: 0 auto;
}

.cadastro_ingressante {
  display: flex;
  justify-content: center;
  width: 100%;
  height: calc(100vh - 16px);
  align-items: center;
}

.input{  
  background-color: white;
  border: 2px solid rgb(22, 113, 187);
  border-radius: 6px; 
  display: inline-block;
  font: inherit;  
  padding: 4px 2.8em 4px 4px;
  margin: 0;      
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  -webkit-appearance: none;
  -moz-appearance: none;
  margin-top: 5px;
  margin-bottom: 10px;
}

.card{ 
  max-width: 600px;
  border: 2px solid rgb(22, 113, 187);
  border-radius: 10px;
  width: 250px;
  overflow: hidden;
}

.gravar {
	background-color:#319e4e;
	border-radius:9px;
	border:1px solid #203822;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:17px;
	padding:5px 5px;
	text-decoration:none;
	text-shadow:0px 0px 0px #788276;
  width: 40%;
}

.gravar:hover {
	background-color:#5cbf2a;
}

.gravar:active {
	position:relative;
	top:1px;
}

.voltar {
	background-color:#d0d953;
	border-radius:9px;
	border:1px solid #a6ba34;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:Arial;
	font-size:17px;
	padding:5px 5px;
	text-decoration:none;
	text-shadow:0px 0px 0px #788276;
  width: 35%;
}

.voltar:hover {
	background-color:#759663;
}

.voltar:active {
	position:relative;
	top:1px;
}

.button {
  display: flex;
  justify-content: space-between;
  margin: 15px;
}

h2 {
  color: #203822;
}

.title {
  background-color:rgb(22, 113, 187); 
  text-align: center;  
  font-size: 24px;
  color: white; 
  padding: 8px;
  margin-bottom: 8px;
}

select {
  background-color: white;
  border: 2px solid rgb(22, 113, 187);
  border-radius: 6px; 
  display: inline-block;
  font: inherit;  
  padding: 4px 2.8em 4px 4px;
  margin: 0;      
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  -webkit-appearance: none;
  -moz-appearance: none;
  margin-top: 5px;
  margin-bottom: 10px;
  cursor: pointer;
}

select.classic {
  background-image:
    linear-gradient(45deg, transparent 50%, white 50%),
    linear-gradient(135deg, white 50%, transparent 50%), 
    radial-gradient(rgb(22, 113, 187), rgb(22, 113, 187));
    /* linear-gradient(to right,rgb(22, 113, 187), rgb(22, 113, 187)); */
    
  background-position: 
    calc(100% - 14px) 50%,
    calc(100% - 7px) 50%,
    calc(100% - 4px) 50%;
  background-size: 
    7px 7px,
    7px 7px,
    20px 20px;
  background-repeat: no-repeat;
}

select.classic:after {
  content: " - Remember this";
  background-color: yellow;
  color: red;
  font-weight: bold;
}
</style>
