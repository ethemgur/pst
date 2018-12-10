<script>
export default {
  created() {
    this.current = this.$f7.params.id
  },
  methods: {
    navigateURL() {
      if (this.current === 21) {

        this.$f7.views.main.loadPage('/survey-satisfaction/0')
      } else {
        this.current += 1
        this.$f7.views.main.loadPage(`/survey-bdi/${this.current}`)
      }
    },
    select(c) {
      try {
        const score = this.questions[this.current].choices.indexOf(c) + 1
        const total = this.$db("bdi")
        this.$db("bdi", score + total)
      } catch (e) {
        this.$db("bdi", score)
      }
    },
  },
  data() {
    return {
      current: 0,
      questions: [
        {
          id: 1,
          choices: [
            'Kendimi üzgün hissetmiyorum',
            'Kendimi üzgün hissediyorum',
            'Her zaman için üzgünüm ve kendimi bu duygudan kurtaramıyorum',
            'Öylesine üzgün ve mutsuzum ki dayanamıyorum',
          ],
        },
        {
          id: 2,
          choices: [
            'Gelecekten umutsuz değilim',
            'Geleceğe biraz umutsuz bakıyorum',
            'Gelecekten beklediğim hiçbir şey yok',
            'Benim için bir gelecek yok ve bu durum düzelmeyecek',

          ],
        },
        {
          id: 3,
          choices: [
            'Kendimi başarısız görmüyorum',
            'Çevremdeki pek çok kişiden daha fazla başarısızlıklarım oldu sayılır',
            'Geriye dönüp baktığımda çok fazla başarısızlığımın olduğunu görüyorum',
            'Kendimi tümüyle başarısız bir insan olarak görüyorum',
          ],
        },
        {
          id: 4,
          choices: [
            'Her şeyden eskisi gibi zevk alabiliyorum',
            'Her şeyden eskisi gibi zevk alamıyorum',
            'Artık hiçbir şeyden gerçek bir zevk alamıyorum',
            'Bana zevk veren hiçbir şey yok. Her şey çok sıkıcı',
          ],
        },
        {
          id: 5,
          choices: [
            'Kendimi suçlu hissetmiyorum',
            'Arada bir kendimi suçlu hissettiğim oluyor',
            'Kendimi çoğunlukla suçlu hissediyorum',
            'Kendimi her an için suçlu hissediyorum',
          ],
        },
        {
          id: 6,
          choices: [
            'Cezalandırıldığımı düşünmüyorum',
            'Bazı şeyler için cezalandırılabileceğimi hissediyorum',
            'Cezalandırılmayı bekliyorum',
            'Cezalandırıldığımı hissediyorum',
          ],
        },
        {
          id: 7,
          choices: [
            'Kendimden hoşnuttum',
            'Kendimden pek hoşnut değilim',
            'Kendimden hiç hoşlanmıyorum',
            'Kendimden nefret ediyorum',
          ],
        },
        {
          id: 8,
          choices: [
            'Kendimi diğer insanlardan daha kötü görmüyorum',
            'Kendimi zayıflıklarım ve hatalarım için eleştiriyorum',
            'Kendimi hatalarım için çoğu zaman suçluyorum',
            'Her kötü olayda kendimi suçluyorum',
          ],
        },
        {
          id: 9,
          choices: [
            'Kendimi öldürmek gibi düşüncelerim yok',
            'Bazen kendimi öldürmeyi düşünüyorum, fakat bunu yapmam',
            'Kendimi öldürebilmeyi isterdim',
            'Bir fırsatını bulsam kendimi öldürürdüm',
          ],
        },
        {
          id: 10,
          choices: [
            'Her zamankinden daha fazla ağladığımı sanmıyorum',
            'Eskisine göre şu sıralarda daha fazla ağlıyorum',
            'Şu sıralarda her an ağlıyorum',
            'Eskiden ağlayabilirdim ama şu sıralarda istesem de ağlayamıyorum',
          ],
        },
        {
          id: 11,
          choices: [
            'Her zamankinden daha fazla sinirli değilim',
            'Her zamankinden daha kolayca sinirleniyor ve kızıyorum',
            'Çoğu zaman sinirliyim',
            'Eskiden sinirlendiğim şeylere bile  artık sinirlenemiyorum',
          ],
        },
        {
          id: 12,
          choices: [
            'Diğer insanlara karşı ilgimi kaybetmedim',
            'Eskisine göre insanlarla daha az ilgiliyim',
            'Diğer insanlara karşı ilgimin çoğunu kaybettim',
            'Diğer insanlara karşı hiç ilgim kalmadı',
          ],
        },
        {
          id: 13,
          choices: [
            'Kararlarımı eskisi kadar kolay ve rahat verebiliyorum',
            'Şu sıralarda kararlarımı vermeyi erteliyorum',
            'Kararlarımı vermekte oldukça güçlük çekiyorum',
            'Artık hiç karar veremiyorum',
          ],
        },
        {
          id: 14,
          choices: [
            'Dış görünüşümün eskisinden daha kötü olduğunu sanmıyorum',
            'Yaşlandığımı ve çekiciliğimi kaybettiğimi düşünüyor ve üzülüyorum',
            'Dış görünüşümde artık değiştirilmesi mümkün olmayan olumsuz değişiklikler olduğunu hissediyorum',
            'Çok çirkin olduğumu düşünüyorum',
          ],
        },
        {
          id: 15,
          choices: [
            'Eskisi kadar iyi çalışabiliyorum',
            'Bir işe başlayabilmek için eskisine göre kendimi daha fazla zorlamam gerekiyor',
            'Hangi iş olursa olsun yapabilmek için kendimi çok zorluyorum',
            'Hiçbir iş yapamıyorum',
          ],
        },
        {
          id: 16,
          choices: [
            'Eskisi kadar rahat uyuyabiliyorum',
            'Şu aralar eskisi kadar rahat uyuyamıyorum',
            'Eskisine göre 1 ya da 2 saat erken uyanıyor ve tekrar uyumakta zorluk çekiyorum',
            'Eskisine göre çok erken uyanıyor ve tekrar uyuyamıyorum',
          ],
        },
        {
          id: 17,
          choices: [
            'Eskisine kıyasla daha çok yorulduğumu sanmıyorum',
            'Eskisinden daha çabuk yoruluyorum',
            'Şu aralar neredeyse her şey beni yoruyor',
            'Öyle yorgunum ki hiçbir şey yapamıyorum',
          ],
        },
        {
          id: 18,
          choices: [
            'İştahım eskisinden çok farklı değil',
            'İştahım eskisinden farklı değil',
            'Şu sıralar iştahım epey kötü',
            'Artık hiç iştahım yok',
          ],
        },
        {
          id: 19,
          choices: [
            'Son zamanlarda pek fazla kilo kaybettiğimi sanmıyorum',
            'Son zamanlarda istemediğim halde 3 kilodan fazla kaybettim',
            'Son zamanlarda istemediğim halde 5 kilodan fazla kaybettim',
            'Son zamanlarda istemediğim halde 7 kilodan fazla kaybettim',
          ],
        },
        {
          id: 20,
          choices: [
            'Sağlığım beni endişelendirmiyor',
            'Son zamanlarda ağrı, sızı, mide bozukluğu, kabızlık gibi sorunlarım var',
            'Ağrı, sızı gibi bu sıkıntıların beni epey endişelendirdiği için başka şeyleri düşünmek zor geliyor',
            'Bu tür sıkıntılar beni öylesine endişelendiriyor ki artık başka hiçbir şey düşünemiyorum',
          ],
        },
        {
          id: 21,
          choices: [
            'Son zamanlarda cinsel yaşantımda dikkatimi çeken bir şey olmadı',
            'Eskisine oranla cinsel konularla daha az ilgileniyorum',
            'Şu sıralar cinsellikle pek ilgili değilim',
            'Artık cinsellikle hiçbir ilgim kalmadı',
          ],
        },
      ],
    }
  },
}
</script>
