<script>
export default {
  created() {
    this.current = this.$f7.params.id
  },
  methods: {
    navigateURL() {
      if (this.current === 6) {
        this.$f7.views.main.loadPage('/survey-stress/0')
      } else {
        this.current += 1
        this.$f7.views.main.loadPage(`/survey-satisfaction/${this.current}`)
      }
    },
  },
  data() {
    return {
      current: 0,
      choices: [
        'Kesinlikle katılmıyorum',
        'Katılmıyorum',
        'Biraz katılmıyorum',
        'Biraz katılıyorum',
        'Katılıyorum',
        'Kesinlikle katılıyorum',
      ],
      questions: [
        {
          id: 1,
          text: 'Hayatım birçok yönlerden idealimdekine yakın',
        },
        {
          id: 2,
          text: 'Hayat şartlarım mükemmel',
        },
        {
          id: 3,
          text: 'Hayatımdan memnunum',
        },
        {
          id: 4,
          text: 'Hayatım, yakın çevremdekilerin çoğunun hayatından daha iyi',
        },
        {
          id: 5,
          text: 'Hayattan şimdiye kadar istediğim önemli şeyleri elde ettim',
        },
        {
          id: 6,
          text: 'Eğer hayata yeniden başlasaydım hemen hemen hiçbir şeyi değiştirmezdim',
        },
      ],
    }
  },
}
</script>
