<template>
  <popper arrow="arrow"
          @open:popper="changePopperFlag"
          @close:popper="changePopperFlag">
    <div class="flat"
         :class="[{flat_choice:this.popperFlag},{none_flat:this.flatInfo.plan_type===null},{marginal:this.flatInfo.marginal},{renovation_flat:this.flatInfo.renovation}]">
      <div class="triangle_installment"
           v-show="this.flatInfo.installment"></div>
      <div class="subsidy"
           v-show="this.flatInfo.subsidy">s
      </div>
      <div>{{ this.flatInfo.plan_type }}</div>
    </div>
    <template #content>
      <div class="popper">
        <div>Цена: {{ this.flatInfo.cost.toLocaleString('ru') }} руб</div>
        <div>Тип: {{ this.flatInfo.type }}</div>
        <div>Этаж: {{ this.flatInfo.floor }}</div>
        <div>Номер кв: {{ this.flatInfo.number }}</div>
        <div>Площадь: {{ this.flatInfo.square }} кв.м</div>
        <div>Статуc: {{ this.flatInfo.status }}</div>
        <div v-show="this.flatInfo.plan_type">Планировка: {{ this.flatInfo.plan_type }}</div>
        <div v-show="this.flatInfo.subsidy">Субсидированная</div>
        <div v-show="this.flatInfo.marginal">Мaржинальная</div>
        <div v-show="this.flatInfo.renovation">C ремонтом</div>
        <div v-show="this.flatInfo.installment">C рассрочкой</div>

      </div>
    </template>
  </popper>
</template>

<script>
import Popper from "vue3-popper";

export default {
  name: "VFlat",
  components: {
    Popper,
  },
  props: ['flat', 'allFlats'],
  data() {
    return {
      popperFlag: false,
    }
  },
  computed: {
    flatInfo: function () {
      return Object.entries(this.allFlats).filter(flatInfo => flatInfo[0] === this.flat.id)[0][1]
    },
  },
  methods: {
    changePopperFlag() {
      this.popperFlag = !this.popperFlag
    },
  }
}
</script>

<style lang="scss">
.flat {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  height: 17px;
  width: 17px;
  font-size: 7px;
  background-color: gray;
  color: white;
  border-radius: 2px;
  position: relative;

  .triangle_installment {
    position: absolute;
    right: 0;
    top: 0;
    border: 3px solid transparent;
    border-top: 3px solid red;
    border-right: 3px solid red;
  }

  .subsidy {
    position: absolute;
    left: 1px;
    top: -1px;
    color: black;
  }
}

.flat:hover {
  background-color: black;
}

.flat:active {
  background-color: black;
  opacity: 0.5;
}

.flat_choice {
  background-color: black;
}

.marginal {
  border-bottom: 3px solid seagreen;
  margin-bottom: 3px;
}

.renovation_flat {
  background-color: orange;
}

.none_flat {
  margin: 2.5px;
  height: 12px;
  width: 12px;
  background-color: gray;
  opacity: 0.5;
}

.popper {
  background-color: white;
  border-radius: 2px;
  padding: 5px;
  filter: drop-shadow(0px 0px 7px rgba(0, 0, 0, 0.25));

  #arrow:before {
    background-color: #FFFFFF;
    visibility: visible;
  }
}
</style>