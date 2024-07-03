<template>
 <section class="container">
    <!-- FORMULARIO -->
    <form class="formulario">

      <label for="input1">Color de fondo:</label>
      <input v-model="colorFondo" type="text" name="" />
      <br />
      <br />

      <label for="input2">color de texto</label>
      <input v-model="colorTexto" type="text" name="" />
      <br />
      <br />

      <label>
        Mostrar texto
        <input v-model="mostrarTexto" type="checkbox" name="" />
      </label>
      <br />
      <br />

      <label for="input4">Borde</label>
      <input v-model="borde" type="range" id="input4" name="input4" min="0" max="200" step="1" />
      <br />
      <br />

      <label>Contenido actual</label>
      <input v-model="contenidoTextual" type="text" name="" value="" maxlength="30" />
      <br />
      <br />

      <!-- <label>
        Tipografía:
        <select v-model="tipografiaTexto" name="tipografia" >
          <option value="Impact">Impact</option>
          <option value="'Brush Script MT'">Brush Script</option>
          <option value="Georgia">Georgia</option>
          <option value="'Arial Black'">Arial Black</option>
          <option value="Garamond">Garamond</option>
        </select> </label -->

      <label>
        Tipografía:
        <select v-model="selectTipoLetra" name="tipografia">
          <option v-for="tipografia in tipografiaTexto" :key="tipografia" :value="tipografia">
            {{ tipografia }}
          </option>
        </select> 
      </label><br /><br />

      <label>
        Opaco
        <input v-model="opacidadCuadro" type="checkbox" name="" /></label><br /><br />

      <label>
        Tamaño de letra
        <input v-model="tamañoTexto" type="radio" id="pequenio" name="tamano" value="pequeño" />
        <label for="pequeño">Pequeño</label>

        <input v-model="tamañoTexto" type="radio" id="mediano" name="tamano" value="mediano" />
        <label for="mediano">Mediano</label>

        <input v-model="tamañoTexto" type="radio" id="grande" name="tamano" value="grande" />
        <label for="grande">Grande</label> </label><br /><br />
    </form>

    <!-- CUADRO DINAMICO -->
    <div class="cuadroDinamico"
      :style="{ backgroundColor: colorFondo, color: colorTexto, fontFamily: selectTipoLetra, borderRadius: borde + 'px', }"
      :class="{
        opacidad: opacidadCuadro === true,
        textoPequeño: tamañoTexto === 'pequeño',
        textoMediano: tamañoTexto === 'mediano',
        textoGrande: tamañoTexto === 'grande',
      }">
      <h1 v-if="mostrarTexto">{{ contenidoTextual }}</h1>
    </div>

  </section>
    
</template>

<script>
export default {
  name: "formularioVue",
  data() {
    return {
      colorFondo: "",
      colorTexto: "",
      mostrarTexto: "",
      selectTipoLetra: "",
      borde: 0,
      contenidoTextual: "",
      tipografiaTexto: [
        "Impact",
        "Brush Script MT",
        "Georgia",
        "Arial Black",
        "Garamond",
      ],
      opacidadCuadro: "",
      tamañoTexto: "",
    };
  },
};

</script>

<style scoped>
.formulario {
  display: flex;
  flex-direction: column;
  padding: 20px;
  width: 25%;
  background-color: cadetblue;
}

.container {
  display: flex;
  justify-content: space-around;
}

.cuadroDinamico {
  width: 400px;
  height: 400px;
  border: solid 1px black;
  text-align: center;
  line-height: 400px;
  font-family: "Courier New", Courier, monospace;
}

.opacidad {
  opacity: 0.5;
}

.textoPequeño {
  font-size: 12px;
}

.textoMediano {
  font-size: 18px;
}

.textoGrande {
  font-size: 24px;
}

</style>
