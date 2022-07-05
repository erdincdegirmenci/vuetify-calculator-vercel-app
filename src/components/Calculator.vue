<template>
  <v-container style="max-width: 400px; text-align: -webkit-center; margin-top: 150px;">
   XRT-CALCULATORr
    <v-row>
      <v-col>
            <v-col md="10">      
                <v-text-field v-model="calculatorValue" ></v-text-field>      
              <v-btn  class="mr-4 mt-2 "  v-for="n in calculatorElement" :key="n" :class="{'deep-orange darken-4' :  n === 'C' ||  n === '/' ||  n === '*' ||  n === '+' ||  n === '=' ||  n === '-' ||  n === '%' ||  n === '.' }"  fab dark @click="action(n)">
                <v-icon>{{n}}</v-icon>
              </v-btn>
            </v-col>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
 export default {
   name: "Calculator",
   data() {
      return {
         operator: null,
         previousCalculatorValue: "",
         calculatorValue: 0,
         calculatorElement: [
            "C",
            "*",
            "/",
            "-",
            7,
            8,
            9,
            "+",
            4,
            5,
            6,
            "%",
            1,
            2,
            3,
            "=",
            0,
            ".",
         ],
      };
   },
   methods: {
      action(n) {
        console.log(n)
         //    Append Values
         if (!isNaN(n) || n === ".") {
            this.calculatorValue = n;
         }
         //  Clear value
         if (n === "C") {
            this.calculatorValue = 0;
         }
         //  Archmetic Operator
         if (["/", "+", "*", "-"].includes(n)) {
            this.operator = n;
            this.previousCalculatorValue = this.calculatorValue;
            // this.calculatorValue = "";
         }
         //  Percantage
         if (n === "%") {
            this.calculatorValue = this.calculatorValue / 100 + "";
         }
         if (n === "=") {
            this.calculatorValue = eval(
               this.previousCalculatorValue +
                  this.operator +
                  this.calculatorValue
            );
            console.log(eval);
            this.previousCalculatorValue = "";
            this.operator = null;
         }
      },
   },
};
</script>
<style scoped>
i {
   font-style: inherit;
}
</style>
