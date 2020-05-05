<template>
  <q-page class="q-pa-lg" >
   <h5 class=q-mt-none>Help</h5>
   <p>Lorem ipsum dolor sit amet, vix saepe verterem antiopam et, vel reque laoreet incorrupte cu, vix ad enim reque probatus. Eros omittam eu his, quo esse magna aperiam et, eum an utinam aliquip maiestatis. Pri dolorem appareat ea. Ut cum offendit pertinax. Sed ei aeterno elaboraret, ad quaestio aliquando similique vim.</p>
   <p>Te vis molestie placerat. Nam id magna commodo consetetur, an doctus lobortis vel, eum electram intellegam cu. Doming eripuit ea nec. Vidit everti ei usu, stet vero posidonium ex mei. Ei pro vero ubique consectetuer. Hinc mucius discere ut sea, cu paulo verear sed. Id eam falli option dissentiet.</p>
   <Todo message="nice">
      <p>{{message}}</p>
   </Todo>
  </q-page>
</template>

<script>
import Todo from './Todo.vue'
export default {
  name: 'PageIndex',
  components:{
   Todo
  }
}
</script>
