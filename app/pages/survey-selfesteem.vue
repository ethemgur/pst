<script>
export default {
  created() {
    this.current = this.$f7.params.id
  },
  methods: {
    navigateURL() {
      if (this.current === 10) {
        this.$f7.views.main.loadPage('/survey-bdi/0')
      } else {
        this.current += 1
        this.$f7.views.main.loadPage(`/survey-selfesteem/${this.current}`)
      }
    },
  },
  data() {
    return {
      current: 0,
      choices: [
        'Çok doğru',
        'Doğru',
        'Yanlış',
        'Çok yanlış',
      ],
      questions: [
        {
          id: 1,
          text: 'Kendimi en az diğer insanlar kadar değerli buluyorum..',
        },
        {
          id: 2,
          text: 'Bazı olumlu özelliklerim olduğunu düşünüyorum.',
        },
        {
          id: 3,
          text: 'Genelde kendimi başarısız biri olarak görme eğilimindeyim.',
        },
        {
          id: 4,
          text: 'Ben de diğer insanların bir çoğunun yapabildiği kadar bir şeyler yapabilirim.',
        },
        {
          id: 5,
          text: 'Kendimde gurur duyacak fazla bir şey bulamıyorum.',
        },
        {
          id: 6,
          text: 'Kendime karşı olumlu bir tutum içerisindeyim.',
        },
        {
          id: 7,
          text: 'Genel olarak kendimden memnunum.',
        },
        {
          id: 8,
          text: 'Kendime karşı daha fazla saygı duyabilmeyi isterdim.',
        },
        {
          id: 9,
          text: 'Bazen kesinlikle kendimin bir işe yaramadığını düşünüyorum.',
        },
        {
          id: 10,
          text: 'Bazen kendimin hiç de yeterli olmadığımı düşünüyorum.',
        },
      ],
    }
  },
}
</script>
