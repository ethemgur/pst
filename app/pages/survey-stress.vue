<script>
export default {
  created() {
    this.current = this.$f7.params.id
  },
  methods: {
    navigateURL() {
      if (this.current === 14) {
        this.$f7.views.main.loadPage('/step12/')
      } else {
        this.current += 1
        this.$f7.views.main.loadPage(`/survey-stress/${this.current}`)
      }
    },
  },
  data() {
    return {
      current: 0,
      choices: [
        'Hiçbir Zaman',
        'Neredeyse Hiçbir Zaman',
        'Bazen',
        'Oldukça Sık',
        'Çok Sık',
      ],
      questions: [
        {
          id: 1,
          text: 'Geçen ay, beklenmedik bir şeylerin olması nedeniyle ne sıklıkta rahatsızlık duydunuz?',
        },
        {
          id: 2,
          text: 'Geçen ay, yaşamınızdaki önemli şeyleri kontrol edemediğinizi ne sıklıkta hissettiniz?',
        },
        {
          id: 3,
          text: 'Geçen ay, kendinizi ne sıklıkta sinirli ve stresli hissettiniz?',
        },
        {
          id: 4,
          text: 'Geçen ay, ne sıklıkta gündelik zorlukların üstesinden başarıyla geldiniz?',
        },
        {
          id: 5,
          text: 'Geçen ay, yaşamınızda ortaya çıkan önemli değişikliklerle etkili bir şekilde başa çıktığınızı ne sıklıkta hissettiniz?',
        },
        {
          id: 6,
          text: 'Geçen ay, kişisel sorunlarınızı ele alma yeteneğinize ne sıklıkta güven duydunuz?',
        },
        {
          id: 7,
          text: 'Geçen ay, her şeyin yolunda gittiğini ne sıklıkta hissettiniz?',
        },
        {
          id: 8,
          text: 'Geçen ay, ne sıklıkta yapmanız gereken şeylerle başa çıkamadığınızı fark ettiniz?',
        },
        {
          id: 9,
          text: 'Geçen ay, yaşamınızdaki zorlukları ne sıklıkta kontrol edebildiniz?',
        },
        {
          id: 10,
          text: 'Geçen ay, ne sıklıkta her şeyin üstesinden geldiğinizi hissettiniz?',
        },
        {
          id: 11,
          text: 'Geçen ay, ne sıklıkta kontrolünüz dışında gelişen olaylar yüzünden öfkelendiniz?',
        },
        {
          id: 12,
          text: 'Geçen ay, kendinizi ne sıklıkta başarmak zorunda olduğunuz şeyleri düşünürken buldunuz?',
        },
        {
          id: 13,
          text: 'Geçen ay, ne sıklıkta zamanınızı nasıl kullanacağınızı kontrol edebildiniz?',
        },
        {
          id: 14,
          text: 'Geçen ay, ne sıklıkta problemlerin üstesinden gelemeyeceğiniz kadar biriktiğini hissettiniz?',
        },
      ],
    }
  },
}
</script>
