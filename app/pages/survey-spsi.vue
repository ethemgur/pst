<script>
export default {
  created() {
    this.current = this.$f7.params.id
  },
  methods: {
    navigateURL() {
      if (this.current === 25) {
        this.$f7.views.main.loadPage('/survey-selfesteem/0')
      } else {
        this.current += 1
        this.$f7.views.main.loadPage(`/survey-spsi/${this.current}`)
      }
    },
  },
  data() {
    return {
      current: 0,
      choices: [
        'Benim için hiç doğru değil',
        'Benim için birazcık doğru',
        'Benim için kısmen doğru',
        'Benim için çok doğru',
        'Benim için tamamen doğru',
      ],
      questions: [
        {
          id: 1,
          text: 'Çözmem gereken önemli bir sorunum olduğunda, kendimi tehdit edilmiş ve korkmuş hissederim',
        },
        {
          id: 2,
          text: 'Karar verirken, bütün seçenekleri yeterince dikkatli bir şekilde değerlendirmem',
        },
        {
          id: 3,
          text: 'Önemli bir karar almam gerektiği zaman kendimi gergin hissederim ve kendimden emin olamam',
        },
        {
          id: 4,
          text: 'Bir sorunu çözmek için ilk baştaki çabalarım başarısız olduğunda, vazgeçmeyip kolayca pes etmezsem sonunda iyi bir çözüm bulacağımın farkındayımdır',
        },
        {
          id: 5,
          text: 'Bir sorunum olduğunda, çözülebileceğine inanırım',
        },
        {
          id: 6,
          text: 'Kendim çözmeye çalışmadan önce, bir sorunun kendiliğinden çözülüp çözülmeyeceğini görmek için beklerim',
        },
        {
          id: 7,
          text: 'Bir sorunu çözmede ilk çabalarım başarısız olduğu zaman çok fazla hayal kırıklığı yaşarım',
        },
        {
          id: 8,
          text: 'Zor bir sorunla karşılaştığımda, ne kadar çok çalışırsam çalışayım kendi başıma çözebileceğimden şüphe ederim.',
        },
        {
          id: 9,
          text: 'Hayatımda bir sorun ortaya çıktığında, çözmeye çalışmayı olabildiğince ertelerim.',
        },
        {
          id: 10,
          text: 'Sorunlarla uğraşmaktan kaçınmak için hayatımın akışını değiştiririm.',
        },
        {
          id: 11,
          text: 'Zor sorunlar beni üzer ve telaşlandırır',
        },
        {
          id: 12,
          text: 'Vermem gereken bir karar olduğunda, her seçeneğin olumlu ve olumsuz sonuçlarını tahmin etmeye çalışırım',
        },
        {
          id: 13,
          text: 'Hayatımda sorunlar ortaya çıktığında, mümkün olan en kısa süre içerisinde onları çözmek isterim',
        },
        {
          id: 14,
          text: 'Bir sorunu çözmeye çalıştığımda, aklıma gelen ilk iyi fikirle hareket ederim',
        },
        {
          id: 15,
          text: 'Zor bir sorunla karşılaştığımda, yeterince gayretli çalışırsam onu tek başıma çözebileceğime inanırım',
        },
        {
          id: 16,
          text: 'Çözmem gereken bir sorun olduğunda, ilk yaptığım işlerden birisi sorun hakkında olabildiğince fazla bilgi toplamaktır',
        },
        {
          id: 17,
          text: 'Hayatımdaki sorunları çözmeyi, bıçak kemiğe dayanıncaya kadar ertelerim',
        },
        {
          id: 18,
          text: 'Sorunlardan kaçmaya onları çözmekten daha fazla zaman harcıyorum',
        },
        {
          id: 19,
          text: 'Bir sorunu çözmeye çalışmadan önce, tam olarak neye ulaşmak istediğimi bilebilmek için kendime bir hedef belirlerim',
        },
        {
          id: 20,
          text: 'Bir karar vermem gerektiği zaman, her bir seçeneğin olumlu ve olumsuz yönlerini düşünmek için zaman harcamam',
        },
        {
          id: 21,
          text: 'Bir sorunu çözdüğümde, sorunla ilgili durumun olumlu yönde ne kadar değiştiğini olabildiğince dikkatli bir biçimde değerlendirmeye çalışırım',
        },
        {
          id: 22,
          text: 'Bir sorunum olduğunda, sorunu olumlu yönde faydalanılabilecek bir fırsat olarak görmeye çalışırım',
        },
        {
          id: 23,
          text: 'Bir sorunu çözmeye çalıştığımda, olabildiğince fazla çözüm seçeneği düşünmeye çalışırım; ta ki aklıma başka bir düşünce gelmeyinceye kadar',
        },
        {
          id: 24,
          text: 'Karar alırken, her seçeneğin sonuçlarını düşünmeden içimden gelen duygularla hareket ederim',
        },
        {
          id: 25,
          text: 'Karar vermem söz konusu olduğunda çok fazla düşünmeden hareket ederim',
        },
      ],
    }
  },
}
</script>
