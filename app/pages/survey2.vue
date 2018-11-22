<template>
  <div data-page="cards" class="page kitchen-sink-material">
    <div class="navbar">
      <div class="navbar-inner">
        <div class="left"><a class="back link icon-only" href="#"><i class="icon icon-back"></i></a></div>
        <div class="center">GENEL TEST</div>
      </div>
    </div>
    <div class="page-content">
      <div data-pagination=".swiper-pagination" data-pagination-type="progress" data-simulate-touch='false' data-next-button=".survey-next-button" class="swiper-container swiper-init ks-demo-slider">
        <div class="swiper-pagination"></div>
        <div class="swiper-wrapper">

          <!-- SPSI SURVEY -->

          <div class="swiper-slide">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">SPSI-R TESTİNE BAŞLA</a>
          </div>

          <div class="swiper-slide" v-for="q in questionsList.spsi.questions">
            <div class="card">
              <div class="card-header"><center>{{q.text}}</center></div>
              <div class="card-content">
                <div class="list-block">
                  <ul>
                    <span v-for="c in questionsList.spsi.choices">
                      <br />
                      <li><a href="#" round="true "class="button button-raised button-fill color-cyan survey-next-button">{{c}}</a></li>
                    </span>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- END OF SPSI SURVEY -->

          <!-- SELF-ESTEEM SURVEY -->

          <div class="swiper-slide">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">ÖZGÜVEN TESTİNE BAŞLA</a>
          </div>

          <div class="swiper-slide" v-for="q in questionsList.selfesteem.questions">
            <div class="card">
              <div class="card-header"><center>{{q.text}}</center></div>
              <div class="card-content">
                <div class="list-block">
                  <ul>
                    <span v-for="c in questionsList.selfesteem.choices">
                      <br />
                      <li><a href="#" round="true "class="button button-raised button-fill color-cyan survey-next-button">{{c}}</a></li>
                    </span>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- END OF SELF-ESTEEM SURVEY -->

          <!-- BDI SURVEY -->

          <div class="swiper-slide">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">BDI TESTİNE BAŞLA</a>
          </div>

          <div class="swiper-slide" v-for="q in questionsList.bdi.questions">
            <div class="card">
              <div class="card-header"><center>Son bir hafta içindeki (bugün dahil) kendi ruh durumunuzu göz önünde bulundurarak size en uygun olan ifadeyi bulunuz.</center></div>
              <div class="card-content">
                <div class="list-block">
                  <ul>
                    <span v-for="c in q.choices">
                      <br />
                      <li><a href="#" class="item-link survey-next-button" style="background-color: #00BCD4; border-radius: 2px; color:white"><p style="padding:2px; font-size:14px"><center>{{c}}</center></p></a></li>
                    </span>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- END OF BDI SURVEY -->

          <!-- SATISFACTION SURVEY -->

          <div class="swiper-slide">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">SATISFACTION TESTİNE BAŞLA</a>
          </div>

          <div class="swiper-slide" v-for="q in questionsList.satisfaction.questions">
            <div class="card">
              <div class="card-header"><center>{{q.text}}</center></div>
              <div class="card-content">
                <div class="list-block">
                  <ul>
                    <span v-for="c in questionsList.satisfaction.choices">
                      <br />
                      <li><a href="#" round="true "class="button button-raised button-fill color-cyan survey-next-button">{{c}}</a></li>
                    </span>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- END OF SATISFACTION SURVEY -->

          <!-- STRESS SURVEY -->

          <div class="swiper-slide">
            <a href="#" class="button button-raised button-fill button-big color-cyan survey-next-button">STRES TESTİNE BAŞLA</a>
          </div>

          <div class="swiper-slide" v-for="q in questionsList.stress.questions">
            <div class="card">
              <div class="card-header"><center>{{q.text}}</center></div>
              <div class="card-content">
                <div class="list-block">
                  <ul>
                    <span v-for="c in questionsList.stress.choices">
                      <br />
                      <li><a href="#" round="true "class="button button-raised button-fill color-cyan survey-next-button">{{c}}</a></li>
                    </span>
                  </ul>
                </div>
              </div>
            </div>
          </div>

          <!-- END OF STRESS SURVEY -->

          <div class="swiper-slide">
            <a href="/step12/" class="button button-raised button-fill button-big color-cyan">TESTİ BİTİR</a>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>
<script>
module.exports = {
  data() {
    return {
      questionsList: {
        stress: {
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
        },
        bdi: {
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
        },
        satisfaction: {
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
        },
        selfesteem: {
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
        },
        spsi: {
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
        },
      },
    }
  },
}
</script>
