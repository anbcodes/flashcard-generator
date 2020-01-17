<template>
  <div id="app">
    <template v-if="front">
      <div class="page" v-for="card in cards" :key="card.answer">
        <div class="front-card card">
          <div class="lesson">Logic</div>
          <div
            :class="'front-text main-text' + (card.tableQ ? ' table' : '')"
            v-html="card.question.replace(/\n/g, '<br>')"
          ></div>
        </div>
      </div>
    </template>
    <template v-else>
      <div class="page" v-for="card in cards" :key="card.answer">
        <div class="back-card card">
          <div class="lesson">Logic</div>
          <div
            :class="'front-text main-text' + (card.tableA ? ' table' : '')"
            v-html="card.answer.replace(/\n/g, '<br>')"
          ></div>
        </div>
      </div>
    </template>
  </div>
</template>

<script>
export default {
  name: "app",
  data: () => ({
    front: true,
    cards: [
      {
        question: 'Negation',
        answer: 'p ~p\n'
              + '----\n'
              + 'T  F\n'
              + 'F  T\n',
        tableA: true,
      },
      {
        question: 'Conjunction',
        answer: 'p q p • q\n'
              + '---------\n'
              + 'T T   T  \n'
              + 'T F   F  \n'
              + 'F T   F  \n'
              + 'F F   F  \n',
        tableA: true,
      },
      {
        question: 'Disjunction',
        answer: 'p q p v q\n'
              + '---------\n'
              + 'T T   T  \n'
              + 'T F   T  \n'
              + 'F T   T  \n'
              + 'F F   F  \n',
        tableA: true,
      },
      {
        question: 'Conditional',
        answer: 'p q p ⊃ q\n'
              + '---------\n'
              + 'T T   T  \n'
              + 'T F   F  \n'
              + 'F T   T  \n'
              + 'F F   T  \n',
        tableA: true,
      },
      {
        question: 'Biconditional',
        answer: 'p q p ≡ q\n'
              + '---------\n'
              + 'T T   T  \n'
              + 'T F   F  \n'
              + 'F T   F  \n'
              + 'F F   T  \n',
        tableA: true,
      },
    ]
  })
};
</script>

<style>
.card {
  margin: 0.1in;
  width: 3.5in;
  height: 2in;
  border-radius: 0.2in;
  border-color: black;
  border-width: 0.02in;
  border-style: solid;
}

.main-text {
  text-align: center;
  position: relative;
  top: 40%;
  transform: translateY(-40%);
  font-family: Arial, Helvetica, sans-serif;
}
.table {
  font-family: monospace;
  font-size: 120%;
}
.lesson {
  position: relative;
  top: 0.13in;
  left: 0.15in;
}
.page {
  width: 8.5in;
  display: flex;
}
body a,
div,
span,
tr,
td {
  white-space: pre;
}
</style>
