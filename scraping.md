```python
import urllib.request
import requests
from bs4 import BeautifulSoup
import sys
import os
import re
import pandas as pd
import random
import time
from datetime import date, timedelta
```


```python
webpage_response = requests.get('https://www.grimmstories.com/language.php?grimm=053&l=ja&r=en')
webpage = webpage_response.content
soup = BeautifulSoup(webpage, "html.parser")
```


```python
for script in soup(["script", "style"]):
    script.decompose()
```


```python
text = soup.get_text()
```


```python
lines= [line.strip() for line in text.splitlines()]
```


```python
text="\n".join(line for line in lines if line)
```


```python
print(text)
```

    白雪姫 (日本語) - Snow-white (英語)
    ZH
    VI
    TR
    RU
    RO
    PT
    PL
    NL
    KO
    JA
    IT
    HU
    FR
    FI
    ES
    EN
    DE
    DA
    グリム童話
    二つの言語にこの物語を比較
    grimmstories.com
    日本語
    白雪姫
    ENGLISH
    Snow-white
    昔、真冬に、雪が羽のようにチラチラと空から降っているとき、窓のところでお后が縫物をしていました。窓枠は黒檀でできており、縫物をして窓から雪を見ている間に、お后は針で指を刺してしまい、３滴の血が雪の上に落ちました。その赤は白い雪の上できれいに見え、お后は「雪のように白く、血のように赤く、窓枠の木のように黒い子供が欲しいわ…」と思いました。
    It was the middle of winter, and the snow-flakes were falling like feathers from the sky, and a queen sat at her window working, and her embroidery-frame was of ebony. And as she worked, gazing at times out on the snow, she pricked her finger, and there fell from it three drops of blood on the snow. And when she saw how bright and red it looked, she said to herself, "Oh that I had a child as white as snow, as red as blood, and as black as the wood of the embroidery frame!" Not very long after she had a daughter, with a skin as white as snow, lips as red as blood, and hair as black as ebony, and she was named Snow-white. And when she was born the queen died. After a year had gone by the king took another wife, a beautiful woman, but proud and overbearing, and she could not bear to be surpassed in beauty by any one. She had a magic looking-glass, and she used to stand before it, and look in it, and say,
    その後まもなくお后は女の子を産みました。その子は雪のように白く、血のように赤く、髪は黒檀のように黒かったので、白雪姫と呼ばれました。子供が生まれたとき、お后は亡くなりました。
    "Looking-glass upon the wall,
    Who is fairest of us all?"
    １年過ぎて王様は新しい妻を迎えました。このお后は美しい人でしたが、高慢で気位が高く、他のだれかが自分より美しいのは我慢できませんでした。お后は不思議な鏡を持っていて、その鏡の前に立ち、映っている自分を見て、「鏡よ、壁の鏡よ、この国で一番美しいのは誰？」と言いました。
    And the looking-glass would answer,
    鏡は答えました。「お后さま、あなたが一番美しい。」
    "You are fairest of them all."
    するとお后は満足しました、鏡は真実を言うと知っていたからです。
    And she was contented, for she knew that the looking-glass spoke the truth. Now, Snow-white was growing prettier and prettier, and when she was seven years old she was as beautiful as day, far more so than the queen herself. So one day when the queen went to her mirror and said,
    しかし白雪姫が成長していって、だんだん美しくなり、７歳のときは昼と同じくらい美しく、お后自身より美しくなりました。そしてあるときお后が「鏡よ、壁の鏡よ、この国で一番美しいのは誰？」と尋ねると、
    "Looking-glass upon the wall,
    鏡は、答えました。「お后さま、あなたはここの誰よりも美しい。だが、白雪姫はもっと美しい。」
    Who is fairest of us all?"
    それでお后はショックをうけ、顔色を黄や緑に変えて妬みました。そのときから白雪姫を見るたびに、心臓が胸で盛り上がるように吐き気がし、娘をとても憎みました。妬みと自尊心が心の中で雑草のようにだんだん高くはびこって、昼も夜も気が休まりませんでした。お后は猟師を呼び、「あの子を森に連れていきなさい。もう見るのは嫌だ。殺して証拠に肺と肝臓を持ってきなさい。」と言いました。猟師は命令に従い、娘を連れ去り、ナイフを引き抜いて白雪姫の無垢な心臓を刺し貫こうとしたとき、娘は泣きだして、「猟師さん、殺さないで。森へ逃げて二度と家へ帰らないわ。」と言いました。
    It answered,
    娘がとても美しいので猟師は可哀そうになって、「じゃあ、逃げろ、可哀そうな子。」と言いましたが、（獣だちがすぐお前を食べてしまうだろう）と思いました。それでももう娘を殺さなくてもよくなったので心から石が転がり出たように思えました。そしてちょうどそのとき子熊が走ってきたので、それを刺して肺と肝臓を切りとり、子供が死んだ証拠としてお后に持っていきました。そして意地悪なお后はそれを食べ、白雪姫の肺と肝臓を食べたと思いこみました。
    "Queen, you are full fair, 'tis true,
    But Snow-white fairer is than you."
    しかし今や可哀そうな子供は大きな森にただ一人で、とても怖くて木々の葉っぱを眺めてどうしたらよいかわかりませんでした。それから走り始め、尖った石を越えイバラを通りぬけ走りました。獣は姫を通りこして走りましたが、危害を加えませんでした。
    This gave the queen a great shock, and she became yellow and green with envy, and from that hour her heart turned against Snow-white, and she hated her. And envy and pride like ill weeds grew in her heart higher every day, until she had no peace day or night. At last she sent for a huntsman, and said, "Take the child out into the woods, so that I may set eyes on her no more. You must put her to death, and bring me her heart for a token." The huntsman consented, and led her away; but when he drew his cutlass to pierce Snow-white's innocent heart, she began to weep, and to say, "Oh, dear huntsman, do not take my life; I will go away into the wild wood, and never come home again." And as she was so lovely the huntsman had pity on her, and said, "Away with you then, poor child;" for he thought the wild animals would be sure to devour her, and it was as if a stone had been rolled away from his heart when he spared to put her to death. Just at that moment a young wild boar came running by, so he caught and killed it, and taking out its heart, he brought it to the queen for a token. And it was salted and cooked, and the wicked woman ate it up, thinking that there was an end of Snow-white.
    足が行く限り走って、ほぼ夕方になり、小さな小屋がみえ、姫は休もうとして中へ入りました。小屋のなかのあらゆるものが小さいのですが、話せないほどきちんとしてきれいでした。食卓があり、その上には白いカバーがかかっていて、７枚の小さな皿がのっていました。それぞれの皿には小さなスプーンがあり、さらに７個のナイフやフォークや７個のカップがありました。壁際に７つの小さなベッドがあり、雪のように白いベッドカバーでおおってありました。
    Now, when the poor child found herself quite alone in the wild woods, she felt full of terror, even of the very leaves on the trees, and she did not know what to do for fright. Then she began to run over the sharp stones and through the thorn bushes, and the wild beasts after her, but they did her no harm. She ran as long as her feet would carry her; and when the evening drew near she came to a little house, and she went inside to rest. Everything there was very small, but as pretty and clean as possible. There stood the little table ready laid, and covered with a white cloth, and seven little plates, and seven knives and forks, and drinking-cups. By the wall stood seven little beds, side by side, covered with clean white quilts. Snow-white, being very hungry and thirsty, ate from each plate a little porridge and bread, and drank out of each little cup a drop of wine, so as not to finish up one portion alone. After that she felt so tired that she lay down on one of the beds, but it did not seem to suit her; one was too long, another too short, but at last the seventh was quite right; and so she lay down upon it, committed herself to heaven, and fell asleep.
    白雪姫はとてもおなかがすいて喉が渇いていたので、それぞれの皿から野菜やパンをいくらか食べ、それぞれのカップから１滴ずつ飲みました。１つのものだけから全部とってしまいたくなかったからです。それから、とても疲れていたので、小さなベッドの一つに横になりましたが、どれも合いませんでした。長すぎたり短すぎたりしましたが、ついに７番目のベッドがいいとわかり、そのベッドに残り、お祈りをして眠りました。
    When it was quite dark, the masters of the house came home. They were seven dwarfs, whose occupation was to dig underground among the mountains. When they had lighted their seven candles, and it was quite light in the little house, they saw that some one must have been in, as everything was not in the same order in which they left it. The first said, "Who has been sitting in my little chair?" The second said, "Who has been eating from my little plate?" The third said, "Who has been taking my little loaf?" The fourth said, "Who has been tasting my porridge?" The fifth said, "Who has been using my little fork?" The sixth said, "Who has been cutting with my little knife?" The seventh said, "Who has been drinking from my little cup?" Then the first one, looking round, saw a hollow in his bed, and cried, "Who has been lying on my bed?" And the others came running, and cried, "Some one has been on our beds too!" But when the seventh looked at his bed, he saw little Snow-white lying there asleep. Then he told the others, who came running up, crying out in their astonishment, and holding up their seven little candles to throw a light upon Snow-white. "O goodness! O gracious!" cried they, "what beautiful child is this?" and were so full of joy to see her that they did not wake her, but let her sleep on. And the seventh dwarf slept with his comrades, an hour at a time with each, until the night had passed. When it was morning, and Snow-white awoke and saw the seven dwarfs, she was very frightened; but they seemed quite friendly, and asked her what her name was, and she told them; and then they asked how she came to be in their house. And she related to them how her step-mother had wished her to be put to death, and how the huntsman had spared her life, and how she had run the whole day long, until at last she had found their little house. Then the dwarfs said, "If you will keep our house for us, and cook, and wash, and make the beds, and sew and knit, and keep everything tidy and clean, you may stay with us, and you shall lack nothing." - "With all my heart," said Snow-white; and so she stayed, and kept the house in good order. In the morning the dwarfs went to the mountain to dig for gold; in the evening they came home, and their supper had to be ready for them. All the day long the maiden was left alone, and the good little dwarfs warned her, saying, "Beware of your step-mother, she will soon know you are here. Let no one into the house." Now the queen, having eaten Snow-white's heart, as she supposed, felt quite sure that now she was the first and fairest, and so she came to her mirror, and said,
    すっかり暗くなって、小屋の持ち主たちが戻ってきました。この人たちは山を掘って鉱石を探していた小人でした。小人たちは７つのろうそくを灯し、小屋の中が明るくなって誰かがそこにいたことにきづきました。というのは、あらゆるものが置いておいたのと同じように並んでいなかったからです。
    "Looking-glass upon the wall,
    最初の小人が「誰が私の椅子に座っていたんだ？」２人目の小人が「誰が私の皿から食べたんだ？」３人目が「誰が私のパンを食べたんだ？」４人目が「誰が私の野菜を食べたんだ？」５人目が「誰が私のフォークを使ったんだ？」６人目が「誰が私のナイフで切ったんだ？」７人目が「誰が私のカップから飲んだんだ？」と言いました。
    Who is fairest of us all?"
    それから最初の小人が周りを見回し、ベッドに小さなくぼみがあるのを見て、「誰が私のベッドに入ったんだ？」と言い、他の小人たちが近づいてきて、それぞれの小人が「誰かが私のベッドにも寝てたんだ。」と言いました。しかし７人目が自分のベッドを見たときそこで眠っている白雪姫を見ました。それで他の小人たちを呼んだので、みんな走って近づいてきて、驚いて叫び、７本の小さなろうそくをもってきて、白雪姫を照らしました。「うわあ！」「わあ！」「なんて可愛い子だ！」と小人たちは叫びました。そしてとても嬉しかったので、白雪姫を起こさないでそのままベッドに寝かせておきました。そして７人目の小人はひとり１時間ずつ仲間と一緒に眠り、そうしてその夜が過ぎました。
    And the glass answered,
    朝になり白雪姫は目覚めて７人の小人たちを見るとこわがりました。しかし小人たちはやさしく、「名前は何ていうの？」と尋ねました。「私の名前は白雪姫よ。」と姫は答えました。「どうしてこの家に来たんだね？」と小人たちは言いました。それで姫は継母が自分を殺させようとしたが、猟師が命を助けてくれ、一日中走って、最後に小人たちの家を見つけた、ということを話しました。
    "Queen, thou art of beauty rare,
    But Snow-white living in the glen
    小人たちは、「家のことをやって、料理し、ベッドを整え、洗濯し、縫ったり編んだりして、全部きちんときれいにしてくれるなら、一緒にいてもいいよ。そうしたらあんたが何も不足ないようにしてあげる。」と小人たちは言いました。「ええ、喜んで。」と白雪姫は言いました。そして姫は小人たちと一緒にいました。姫は小人たちのために家をきちんとしておきました。朝に小人たちは山に行き、銅や金を探し、夜に戻ってきました。その時は夕食は準備ができていなければなりませんでした。姫は一日中一人でした。それでやさしい小人たちは姫に注意して、「継母に注意しなさいよ。あんたがここにいるのがまもなくわかるだろうから。ほんとに誰も家に入れないんだよ。」と言いました。
    With the seven little men
    Is a thousand times more fair."
    しかし、お后は白雪姫の肺と肝臓を食べたと信じていたので、自分がまた一番で最も美しいとしか考えられなくて、鏡のところに行き、言いました。「鏡よ、壁の鏡よ、この国で一番美しいのは誰？」
    Then she was very angry, for the glass always spoke the truth, and she knew that the huntsman must have deceived her, and that Snow-white must still be living. And she thought and thought how she could manage to make an end of her, for as long as she was not the fairest in the land, envy left her no rest. At last she thought of a plan; she painted her face and dressed herself like an old pedlar woman, so that no one would have known her. In this disguise she went across the seven mountains, until she came to the house of the seven little dwarfs, and she knocked at the door and cried, "Fine wares to sell! fine wares to sell!" Snow-white peeped out of the window and cried, "Good-day, good woman, what have you to sell?" - "Good wares, fine wares," answered she, "laces of all colours;"and she held up a piece that was woven of variegated silk. "I need not be afraid of letting in this good woman," thought Snow-white, and she unbarred the door and bought the pretty lace. "What a figure you are, child!" said the old woman, "come and let me lace you properly for once." Snow-white, suspecting nothing, stood up before her, and let her lace her with the new lace; but the old woman laced so quick and tight that it took Snow-white's breath away, and she fell down as dead. "Now you have done with being the fairest," said the old woman as she hastened away. Not long after that, towards evening, the seven dwarfs came home, and were terrified to see their dear Snow-white lying on the ground, without life or motion; they raised her up, and when they saw how tightly she was laced they cut the lace in two; then she began to draw breath, and little by little she returned to life. When the dwarfs heard what had happened they said, "The old pedlar woman was no other than the wicked queen; you must beware of letting any one in when we are not here!" And when the wicked woman got home she went to her glass and said,
    鏡は、答えました。「お后さま、あなたは私に見えるうちで一番美しい。だが、山の向こうの、７人の小人が住むところに、白雪姫はまだ元気に生きている。誰も白雪姫ほど美しい人はいない。」
    "Looking-glass against the wall,
    それでお后はびっくり仰天しました。というのは鏡は決して嘘を言わないと知っているので、猟師が自分を裏切って、白雪姫がまだ生きているとわかったからです。
    Who is fairest of us all?"
    それでお后はどうやって白雪姫を殺そうかと考えに考えました。というのは自分が国中で一番美しくない限り、妬ましさで心が休まらないからです。とうとうやることを思いつくと、お后は顔を塗り、行商の女の服装をし、誰もお后だとわからないようにしました。この変装で、７つの山を越えて７人の小人の家へ行き、戸をたたき、「きれいなものを売ってるよ、とても安い、とても安いよ。」と叫びました。白雪姫は窓から外を覗いて、「こんにちは、おばさん。何を売ってるの？」と叫びました。「いいもの。きれいなもの。いろいろな色のコルセットの紐。」と女は答え、鮮やかな色の絹で織られたものを引っ張りだしました。「きちんとわかる人を入れてもいいわ。」と白雪姫は思い、戸のかんぬきを外し、きれいな紐を買いました。「娘さん、なんてひどいかっこうなの？さあ、一度ちゃんとあなたに結んであげましょう。」とおばあさんは言いました。白雪姫はなにも疑わないでおばあさんの前に立ち、新しい紐で結ばせました。しかしおばあさんはとてもすばやくきつく結んだので、白雪姫は息ができなくなり死んだように倒れました。さあこれで私が一番美しいわ、とお后は心でつぶやき、逃げて行きました。
    And it answered as before,
    それからまもなくして、夜に７人の小人たちが家へ帰ってきました。しかし、愛する白雪姫が床に倒れていて、微かにもうごかず、死んでいるようなのを見て、どんなにショックをうけたことでしょう。小人たちは白雪姫を持ち上げて、とてもきつく締められているのをみたので紐を切りました。すると姫は少し息をし始め、しばらくして生き返りました。小人たちは何が起こったか聞くと、「その行商の女は性悪のお后に違いないよ。私たちがいないときは誰も家に入れないように注意しなさい。」と言いました。
    "Queen, thou art of beauty rare,
    But Snow-white living in the glen
    しかし、性悪の女は家に着くと、鏡の前へいき、尋ねました。「鏡よ、壁の鏡よ、この国で一番美しいのは誰？」
    With the seven little men
    Is a thousand times more fair."
    そして鏡は前と同じように答えました、「お后さま、あなたは私に見えるうちで一番美しい。だが、山の向こうの、７人の小人が住むところに、白雪姫はまだ元気に生きている。誰も白雪姫ほど美しい人はいない。」
    When she heard that she was so struck with surprise that all the blood left her heart, for she knew that Snow-white must still be living. "But now," said she, "I will think of something that will be her ruin." And by witchcraft she made a poisoned comb. Then she dressed herself up to look like another different sort of old woman. So she went across the seven mountains and came to the house of the seven dwarfs, and knocked at the door and cried, "Good wares to sell! good wares to sell!" Snow-white looked out and said, "Go away, I must not let anybody in." - "But you are not forbidden to look," said the old woman, taking out the poisoned comb and holding it up. It pleased the poor child so much that she was tempted to open the door; and when the bargain was made the old woman said, "Now, for once your hair shall be properly combed." Poor Snow-white, thinking no harm, let the old woman do as she would, but no sooner was the comb put in her hair than the poison began to work, and the poor girl fell down senseless. "Now, you paragon of beauty," said the wicked woman, "this is the end of you," and went off. By good luck it was now near evening, and the seven little dwarfs came home. When they saw Snow-white lying on the ground as dead, they thought directly that it was the step-mother's doing, and looked about, found the poisoned comb, and no sooner had they drawn it out of her hair than Snow-white came to herself, and related all that had passed. Then they warned her once more to be on her guard, and never again to let any one in at the door. And the queen went home and stood before the looking-glass and said,
    これを聞くと、恐怖ですべての血が心臓に走りました。というのはお后は白雪姫がまた生きているとはっきりわかったからです。「だけど今度は、本当にお前をお終いにするものを考えてやる。」とお后は言いました。そして自分が知っている魔法の力で、毒の櫛を作りました。それから変装して別のおばあさんの姿になりました。そうして７つの山を越え、７人の小人の家に行き、戸をたたいて、「いいものを売ってるよ。安いよ。安いよ。」と叫びました。白雪姫は外を覗いて、「あっちへ行って。だれも入れられないのよ。」と言いました。「見ることはできるよ。」とおばあさんは言って、毒の櫛を引っ張りだし、持ち上げてみせました。姫はその櫛がとても気に入ったので、自分をごまかして戸を開けました。買い物が終わると、おばあさんは、「さあ一度あんたの髪をちゃんととかしてあげましょう。」と言いました。白雪姫は何も疑わないで、おばあさんに好きなようにさせました。しかし髪に櫛を入れた途端、櫛の中の毒が効いて姫は意識を失って倒れました。「絶世の美女のおまえも今はおしまいさ。」と性悪女は言って逃げて行きました。
    "Looking-glass against the wall,
    しかし幸いにもほぼ夜になっていｔので７人の小人たちが家へ帰ってきました。白雪姫が死んだように床に倒れているのを見たとき、小人たちはすぐに継母のことを疑い、見回して毒の櫛を見つけました。その櫛をはずしたとたん白雪姫は息を吹き返し、起こったことを話しました。すると小人たちはもう一度、用心するように、だれにも戸をあけないように、と注意しました。
    Who is fairest of us all?"
    お后は家で鏡の前へいき、尋ねました。「鏡よ、壁の鏡よ、この国で一番美しいのは誰？」
    And the looking-glass answered as before,
    そして鏡は前と同じように答えました、「お后さま、あなたは私に見えるうちで一番美しい。だが、山の向こうの、７人の小人が住むところに、白雪姫はまだ元気に生きている。誰も白雪姫ほど美しい人はいない。」
    "Queen, thou art of beauty rare,
    But Snow-white living in the glen
    お后は鏡が話すのを聞いて、怒りでぶるぶる震えました。「私の命にかけても白雪姫を殺してやる。」とお后は叫びました。
    With the seven little men
    Is a thousand times more fair."
    そうしてお后は、誰もこれまで来なかった全く秘密の寂しい部屋に入っていき、そこでとても毒のあるリンゴを作りました。外側は赤い頬がついた白でおいしそうに見え、それを見た誰でも欲しくなるけれど、一口食べたら必ず死ぬことになるのです。
    When she heard the looking-glass speak thus she trembled and shook with anger. "Snow-white shall die," cried she, "though it should cost me my own life!" And then she went to a secret lonely chamber, where no one was likely to come, and there she made a poisonous apple. It was beautiful to look upon, being white with red cheeks, so that any one who should see it must long for it, but whoever ate even a little bit of it must die. When the apple was ready she painted her face and clothed herself like a peasant woman, and went across the seven mountains to where the seven dwarfs lived. And when she knocked at the door Snow-white put her head out of the window and said, "I dare not let anybody in; the seven dwarfs told me not." - "All right," answered the woman; "I can easily get rid of my apples elsewhere. There, I will give you one." - "No," answered Snow-white, "I dare not take anything." - "Are you afraid of poison?" said the woman, "look here, I will cut the apple in two pieces; you shall have the red side, I will have the white one." For the apple was so cunningly made, that all the poison was in the rosy half of it. Snow-white longed for the beautiful apple, and as she saw the peasant woman eating a piece of it she could no longer refrain, but stretched out her hand and took the poisoned half. But no sooner had she taken a morsel of it into her mouth than she fell to the earth as dead. And the queen, casting on her a terrible glance, laughed aloud and cried, "As white as snow, as red as blood, as black as ebony! this time the dwarfs will not be able to bring you to life again." And when she went home and asked the looking-glass,
    リンゴが準備できるとお后は顔を塗り、農家のおかみさんの扮装をしました。そうして７つの山を越え、７人の小人の家へ行きました。おかみさんは戸をたたきました。白雪姫は頭を窓から出し、「誰も中へ入れられないの。７人の小人さんたちが禁じたのよ。」と言いました。「どっちでもいいよ。まもなくりんごをおしまいにするからさ。ほら、一つあげるよ。」と女は言いました。「だめよ。私は何ももらっちゃいけないのよ。」と白雪姫は言いました。「毒があると思うのかい？ほら、りんごを半分に割るよ。あんたは赤い方を食べな。私は白い方をたべるからさ。」とおばあさんはいいました。りんごはとても上手に作られていて、赤い方だけに毒が入っていたのです。白雪姫は立派なリンゴが食べたかったのですが、おばあさんがその一部分を食べるのを見たとき、もう我慢ができなくなり、手を伸ばして毒の入った半分を貰いました。しかし、一口口に入れた途端、倒れて死んでしまいました。それからお后は恐ろしい顔で姫を見て、大声で笑い、「雪のように白く、血のように赤く、黒檀のように黒い人、今度は小人たちはお前を二度と目覚めさせられないよ。」と言いました。
    "Looking-glass against the wall,
    お后は家で鏡の前へいき、「鏡よ、壁の鏡よ、この国で一番美しいのは誰？」と尋ねると、鏡はついに「お后さま、あなたがこの国で一番美しい。」と答えました。するとお后の妬み深い心が休まりました。妬み深いこころが休むことができる限りにおいてですが。
    Who is fairest of us all?"
    小人たちは夜家へ帰ってきて、白雪姫が床に倒れているのをみつけました。姫はもう息をしていなくて死んでいました。小人たちは姫を持ち上げて、どくのある何かを見つけられないかとみて調べ、紐をほどき、髪をとかし、水や葡萄酒で姫を洗いましたが、全て無駄で、可哀そうな娘は死んでしまい、死んだままでした。小人たちは棺台に姫をのせ、７人全員がその周りに座り、３日間泣き続けました。
    at last it answered,
    それから小人たちは姫を埋めようとしましたが、姫はまだ生きているように見え、まだ可愛い赤い頬をしていました。小人たちは、「この子を暗い土に埋められないよ。」と言って、周りから見えるように、透明なガラスの棺を作らせ、その中に姫をねかし、棺に金の文字で名前を書き、王様の娘と記しました。それから棺を山の上に置いて、一人がいつもそのそばにいて、番をしました。鳥たちも来て、白雪姫を悼んで泣きました。最初にふくろうが、それからカラスが、最後に鳩が来ました。
    "You are the fairest now of all."
    そして白雪姫は長い、長い間棺のなかに横たわっていましたが、変わらないで、眠っているかのように見えました。というのは、姫は雪のように白く、血のように赤く、髪は黒檀のように黒かったからです。
    Then her envious heart had peace, as much as an envious heart can have. The dwarfs, when they came home in the evening, found Snow-white lying on the ground, and there came no breath out of her mouth, and she was dead. They lifted her up, sought if anything poisonous was to be found, cut her laces, combed her hair, washed her with water and wine, but all was of no avail, the poor child was dead, and remained dead. Then they laid her on a bier, and sat all seven of them round it, and wept and lamented three whole days. And then they would have buried her, but that she looked still as if she were living, with her beautiful blooming cheeks. So they said, "We cannot hide her away in the black ground." And they had made a coffin of clear glass, so as to be looked into from all sides, and they laid her in it, and wrote in golden letters upon it her name, and that she was a king's daughter. Then they set the coffin out upon the mountain, and one of them always remained by it to watch. And the birds came too, and mourned for Snow-white, first an owl, then a raven, and lastly, a dove. Now, for a long while Snow-white lay in the coffin and never changed, but looked as if she were asleep, for she was still as' white as snow, as red as blood, and her hair was as black as ebony. It happened, however, that one day a king's son rode through the wood and up to the dwarfs' house, which was near it. He saw on the mountain the coffin, and beautiful Snow-white within it, and he read what was written in golden letters upon it. Then he said to the dwarfs, "Let me have the coffin, and I will give you whatever you like to ask for it." But the dwarfs told him that they could not part with it for all the gold in the world. But he said, "I beseech you to give it me, for I cannot live without looking upon Snow-white; if you consent I will bring you to great honour, and care for you as if you were my brethren." When he so spoke the good little dwarfs had pity upon him and gave him the coffin, and the king's son called his servants and bid them carry it away on their shoulders. Now it happened that as they were going along they stumbled over a bush, and with the shaking the bit of poisoned apple flew out of her throat. It was not long before she opened her eyes, threw up the cover of the coffin, and sat up, alive and well. "Oh dear! where am I?" cried she. The king's son answered, full of joy, "You are near me," and, relating all that had happened, he said, "I would rather have you than anything in the world; come with me to my father's castle and you shall be my bride." And Snow-white was kind, and went with him, and their wedding was held with pomp and great splendour. But Snow-white's wicked step-mother was also bidden to the feast, and when she had dressed herself in beautiful clothes she went to her looking-glass and said,
    ところが、あるとき、王様の息子が山に入ってきて、一晩泊めてもらうため小人たちの家にいきました。王子は山の上の棺とその中の美しい白雪姫を見て、金の文字で書かれているものを読みました。それで、王子は「棺を貰い受けたい、望みのものを何でも与えよう。」と小人たちに言いました。しかし小人たちは、「世界中の金をもらってもそれと分かれません。」と答えました。それで王子は、「贈り物として貰えないか。というのは白雪姫を見ないでは生きられないからだ。私は最も大切なものとして姫を崇め大切にするつもりだ。」と言いました。こういう風に言うので小人たちは王子が可哀そうになり、棺をあげました。
    "Looking-glass upon the wall,
    Who is fairest of us all?"
    そうして王様の息子は、家来の肩に担がせて棺を運んで行きました。するとたまたま家来が木の切り株につまづいて、その衝撃で白雪姫が食べたりんごの毒のかけらが喉から出ました。そしてまもなく姫は目を開け、棺のふたをあけて、起きあがり、もう一度生き返りました。「まあ、ここはどこ？」と姫は叫びました。王子はすっかり嬉しくなって、「私と一緒にいますよ。」と言って、起こったことを話し、「私は世界中の何よりもあなたを愛しています。私の父の宮殿へ一緒に来て、私の妻になってください。」と言いました。
    The looking-glass answered,
    そして白雪姫は喜んで申し出を受け、王子と一緒に行きました。二人の結婚式はとても見事で豪華に行われました。しかし、白雪姫の性悪な継母も宴に呼ばれました。それで美しい服を着て身支度を整えたとき、鏡の前に行き、「鏡よ、壁の鏡よ、この国で一番美しいのは誰？」と言いました。
    ''O Queen, although you are of beauty rare,
    鏡は答えました。「お后さま、あなたはここで一番美しい。しかし若いお妃ははるかにもっと美しい。」
    The young bride is a thousand times more fair."
    すると性悪な女は呪いの言葉を言って、とても気分が悪くなり、すっかりくさりましたがどうしたらよいかわかりませんでした。はじめは結婚式に行くのはやめようと思いましたが、落ち着かないので、行って若いお妃に会うしかありませんでした。そして入っていくと、白雪姫だとわかり、怒りと恐れで立ちすくみ、動けませんでした。しかし、鉄の靴がすでに火にかけられ、はさみでつかんで運び込まれ、お后の前におかれました。それから真っ赤な熱い靴を履いて踊らされ、とうとう倒れて死にました。
    Then she railed and cursed, and was beside herself with disappointment and anger. First she thought she would not go to the wedding; but then she felt she should have no peace until she went and saw the bride. And when she saw her she knew her for Snow-white, and could not stir from the place for anger and terror. For they had ready red-hot iron shoes, in which she had to dance until she fell down dead.
    二つの言語を比較します:
    DANSK
    DEUTSCH
    ENGLISH
    ESPAÑOL
    SUOMI
    FRANÇAIS
    MAGYAR
    ITALIANO
    日本語
    NEDERLANDS
    POLSKI
    PORTUGUÊS
    ROMÂNĂ
    РУССКИЙ
    TÜRKÇE
    УКРАЇНСЬКА
    TIẾNG VIỆT
    中文
    DANSK
    DEUTSCH
    ENGLISH
    ESPAÑOL
    SUOMI
    FRANÇAIS
    MAGYAR
    ITALIANO
    日本語
    NEDERLANDS
    POLSKI
    PORTUGUÊS
    ROMÂNĂ
    РУССКИЙ
    TÜRKÇE
    УКРАЇНСЬКА
    TIẾNG VIỆT
    中文
    cookies
    grimmstories.com
    Grimms eventyr
    Grimms Märchen
    Grimms' Fairy Tales
    Cuentos de Grimm
    Grimmin sadut
    Contes de Grimm
    Grimm mesék
    Fiabe dei Grimm
    Сказки братьев Гримм
    Grimm Masalları
    Sprookjes van Grimm
    Baśnie braci Grimm
    Contos de Grimm
    Poveşti de Grimm
    Truyện cổ Grimm
    格林童話
    グリム童話
    그림 동화
    andersenstories.com
    Andersens eventyr
    Andersens Märchen
    Andersen's Fairy Tales
    Cuentos de Andersen
    Contes d'Andersen
    Fiabe di Andersen
    Sprookjes van Andersen
    


```python

```
