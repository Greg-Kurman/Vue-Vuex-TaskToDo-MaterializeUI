<template>
  <div class="row">
    <div class=" col s6 offset-s3">
      <h1>Создать задание</h1>
      <form action="" @submit.prevent="submitHandler">
        <div class="input-field  ">
          <input id="title" v-model="title" type="text" class="validate" required>
          <label for="title">Заголовок</label>
          <span class="helper-text" data-error="wrong" data-success="right">проверка</span>
        </div>
        <div class="chips" ref="chips"></div>

        <div class="input-field  ">
          <textarea v-model="description" id="description" class="materialize-textarea" data-length="120"></textarea>
          <label for="description">Описание задания</label>
          <span class="character-counter" style="float: right; font-size: 12px;">{{description.length}}/2048</span>
        </div>

        <input type="text" ref="datepicker">
        <button class="btn" type="submit">Создать задание</button>
      </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Create',
  data: () => ({
    description: '',
    title: '',
    chips: null,
    date: null,
  }),
  mounted() {
    this.chips = M.Chips.init(this.$refs.chips, {
      placeholder: 'Теги задания'
    }),
     this.date = M.Datepicker.init(this.$refs.datepicker, {
        format: 'dd.mm.yyyy',
        defaultDate: new Date(),
        setDefaultDate: true
      });
  },
  methods: {
    submitHandler() {
      const task = {
        title: this.title,
        description: this.description,
        id: Date.now(),
        status: "active",
        tags: this.chips.chipsData,
        date: this.date.date
      }
      console.log(this.$store.dispath('createTask', task))
      console.log(this.$router.push('/list'))

      this.store.dispath('createTask', task)
      this.router.push('/list')
    }
  },
  destroyed() {
    if ( this.date && this.date.destroy) {
      this.date.destroy()
    }

    if ( this.chips && this.chips.destroy) {
      this.chips.destroy()
    }
  },
}
</script>
