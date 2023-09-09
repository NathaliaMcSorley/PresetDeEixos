<script setup>
import ItemCalcular from './ItemCalcular.vue'
import ToolIcon from './icons/IconTool.vue'
import ArrowIcon from './icons/IconArrow.vue'
import RulerIcon from './icons/IconRuler.vue'
import ToolingIcon from './icons/IconTooling.vue'
</script>

<template>
  <ItemCalcular>
    <template #icon>
      <ToolIcon />
    </template>
    <template #heading>Dado de Referencia</template>
    <v-row>
      <v-col>
      <v-text-field label="Numero do desenho: "></v-text-field>
      </v-col>
    </v-row>
    <v-form v-model="form" @submit.prevent="onSubmit">
      <v-row>
        <v-col>
        <v-text-field 
          v-model="diametroReal"
          :rules="[required]"
          clearable 
          label="Diametro Real (mm): ">
        </v-text-field>
        </v-col>
        <v-col>
        <v-text-field 
          v-model="comprimentoReal"
          :rules="[required]"
          clearable 
          label="Comp. Real Total (mm): ">
        </v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
        <v-text-field 
          v-model="medidaFinal"
          :rules="[required]"
          clearable 
          label="Medida Final (mm): ">
        </v-text-field>
        </v-col>
        <v-col>
        <v-text-field 
          v-model="comprimentoChato"
          :rules="[required]"
          clearable 
          label="Compr. do Chato (mm): ">
        </v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
        <v-text-field 
          v-model="chanfroGrau"
          clearable 
          label="Chanfro em graus: ">
        </v-text-field>
        </v-col>
        <v-col>
        <v-text-field 
          v-model="chanfroMilimetro"
          clearable 
          label="Chanfro (mm): ">
        </v-text-field>
        </v-col>
        <v-col>
        <v-text-field 
          v-model="raio"
          :rules="[required]"
          clearable 
          label="Raio (mm): ">  
        </v-text-field>
        </v-col>
      </v-row>
      <v-row>
        <v-col>
        <v-text-field 
          v-model="desbaste"
          :rules="[required]"
          clearable 
          label="Valor Total Desbaste (mm): ">
        </v-text-field>
        </v-col>
      </v-row>
      <v-btn
          :disabled="!form"
          :loading="loading"
          block
          color="success"
          size="large"
          type="submit"
          variant="elevated"
        >
          Calcular
        </v-btn>
    </v-form>
  </ItemCalcular>

  <div v-show="calculo">
    <ItemCalcular>
    <template #icon>
      <ArrowIcon />
    </template>
    <template #heading>Desbaste</template>
    <v-row>
      <v-col>
      <v-text-field label="1 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C2: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C3: "></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
      <v-text-field label="2 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C2: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C3: "></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
      <v-text-field label="3 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C2: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C3: "></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
      <v-text-field label="4 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C2: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C3: "></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
      <v-text-field label="5 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C2: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C3: "></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
      <v-text-field label="6 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C2: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C3: "></v-text-field>
      </v-col>
    </v-row>
  </ItemCalcular>

  <ItemCalcular>
    <template #icon>
      <RulerIcon />
    </template>
    <template #heading>Acabamento</template>
    <v-row>
      <v-col>
      <v-text-field label="1 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C2: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C3: "></v-text-field>
      </v-col>
    </v-row>  
  </ItemCalcular>

  <ItemCalcular>
    <template #icon>
      <RulerIcon />
    </template>
    <template #heading>Raio</template>
    <v-row>
      <v-col>
      <v-text-field label="1 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
    </v-row>  
  </ItemCalcular>

  <ItemCalcular v-show="this.chanfroGrau!=null && this.chanfroGrau!='' || this.chanfroMilimetro!=null && this.chanfroMilimetro!=''">
    <template #icon>
      <ToolingIcon />
    </template>
    <template #heading>Chanfro</template>
    <v-row>
      <v-col>
      <v-text-field label="Angulo: "></v-text-field>
      </v-col>
    </v-row>
    <v-row>
      <v-col>
      <v-text-field label="1 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
    </v-row>  
    <v-row>
      <v-col>
      <v-text-field label="2 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
    </v-row>  
    <v-row>
      <v-col>
      <v-text-field label="3 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
    </v-row>  
    <v-row>
      <v-col>
      <v-text-field label="4 A/B: "></v-text-field>
      </v-col>
      <v-col>
      <v-text-field label="C1: "></v-text-field>
      </v-col>
    </v-row>  
  </ItemCalcular>
  </div>
</template>

<script>
  export default {
    data: () => ({
      form: false,
      diametroReal: null,
      comprimentoReal: null,
      medidaFinal: null,
      comprimentoChato: null,
      chanfroGrau: null,
      chanfroMilimetro: null,
      raio: null,
      desbaste: null,
      loading: false,
      calculo: false,
    }),

    methods: {
      onSubmit () {
        if (!this.form) return
        this.loading = true
        setTimeout(() => (this.loading = false), 2000)
      },
      required (v) {
        if (/[0-9-]+/.test(v)) return true
        return 'Entre um valor numerico.'
      },
    },
  }
</script>
