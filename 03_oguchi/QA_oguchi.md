- Q1:マウスサンプルを使った疾患研究をしているのですが、このエンハンサー領域の解析はヒトサンプルでの解析が適切ということでしょうか。
  - A1: ご質問有難うございます。マウスの5'scRNA-seqのサンプルでも適用可能です。実際にマウスでも解析を別プロジェクトで行っています。
- Q2: 5'でscRNAseqを外注にて行う場合、何か注意が必要でしょうか。
  - A2: ご質問有難うございます。１）Read 1,2共に長め（100bp PEや150bp PEなど）シークエンスすること、２）5' scRNA-seqのライブラリ以外の構造のライブラリもしくはPhiXが10-20%混ざっていること（固定配列の部分にcomplexityを出すため）、この２つが注意点になります。
- Q3: 双方向に転写がみられるbtEはH3K27acやBRD4とかとも相関は見られているのでしょうか？
  - A3: ご質問有難うございます。H3K27acやH3K4me1のシグナルと相関は確認しています。BRD4は調べておりませんでしたが、MED1は相関していました。
- Q4: 確からしいエンハンサー領域を解析可能な量読み取るためには、リード数は通常のscRNA-seqよりも多く（深く）読む必要があるのでしょうか？理解が甘く、基礎的な質問で申し訳ございません。
  - A4: ご質問有難うございます。遺伝子発現解析の時と同等程度、25000-50000 reads/cellで問題ありません。エンハンサー領域をしっかり捉えるにはリード数よりも細胞数（クラスターの中に少なくとも数千細胞）が大事と考えています。
- Q5: UMAPにおいて、通常の遺伝子発現、エンハンサーRNA発現、エンハンサーRNA発現＋通常の遺伝子発現を用いた時に細胞の分離は変化しますか？特異的な細胞はみられますか？
  - A5: ご質問有難うございます。明確に分かれてくるものがあるわけではないが、多少は良くなる印象です。面白いのは転写開始点で見ているのでアイソフォーム毎の発現を見ることも可能です。「ここはロングアイソフォームが、ここはショートアイソフォームが発現している」という違いが見られます。
- Q6: 今後はどのようにこの研究が発展されるとお考えですか？
  - A6: ご質問有難うございます。他の疾患（精神疾患や生活習慣病など）の解明のために、脳などの他の臓器でも同等の解析も可能と思います。また今回見つけたエンハンサー領域でかつマウスでも保存されている領域をゲノム編集で潰して機能を見るなども考えています。
- Q7: エンハンサーRNAは１細胞あたり何種類くらい検出できますか？
  - A7: ご質問有難うございます。分子数はリードのカウントから直接的に推測するのは難しいですが、deduplicate後のリードの0.5%前後がeRNAに対応していると考えます。
- Q8: エンハンサーRNAの発現量はそのままエンハンサーの活性化度合いと解釈できるものなのでしょうか。
  - A8: ご質問有難うございます。おおむね発現量が高ければ活性が高い傾向にあります。
- Q9: BulkのCAGEなどと比較した時にoligo dTによるinternal primingでは何%程度eRNAをキャプチャーできているのでしょうか。
  - A9: ご質問有難うございます。８割程度は両者の方法でオーバーラップしているように思います。
- Q10: Cap由来のGを判定する方法ですが、転写開始点付近のreference配列がpolyGの場合も特定できるのでしょうか？
  - A10: ご質問有難うございます。リファレンスにGがあるところですとCap由来のGだとしてもとReapTECで除くこととなります。PolyGが長いとエンハンサーRNAが取れていないかもしれません。しかしエンハンサーの領域はACGTの出現率が均等なのでGに偏るのは珍しく、大体は網羅できていると考えています。
- Q11: 今回の論文でT細胞に着目したのはどのような理由でしょうか
  - A11: ご質問有難うございます。同定したエンハンサーとGWASのstudyとの統合解析をおこないたいと考えました。１）自己免疫疾患やアレルギー疾患ではGWAS研究が数多く取り組まれているのでデータも豊富であること。２）CD4+のT細胞は免疫の管制塔として重要で、自己免疫疾患、アレルギー疾患にも関わる面白い細胞であること。３）また、採血からT細胞を採取でき、研究しやすいこと、から今回CD4+T細胞ではじめました。
- Q12: 細胞種特異的なエンハンサーが生じるメカニズムはなんでしょうか？（エンハンサー配列の修飾？　転写因子の発現？）
  - A12: ご質問有難うございます。エンハンサー配列はACGTの出現率が均等でいろいろなパターンの配列を作りやすいこと、また細胞種ごとに転写開始点のbindingが異なることが理由と考えています。
- Q13: 同じく理研のHon Chung Chau博士が開発したSCAFEも同様に5‘scRNA-seqを用いてTSSを解析する方法ですが比較するとどのようなメリット、デメリットがあるのでしょうか
  - A13: ご質問有難うございます。メリット①としましては、我々の手法では低発現のエンハンサーも検出しやすいことが挙げられます。というのも、我々は最初にunencoded Gの情報で、リードをfilteringしているのに対して、彼は、まずリードのクラスターを作って、そのクラスターの中にどのくらいunencoded Gを持つリードが存在しているかでfilteringしており、いつfilteringを行っているかが違うからです。メリット②としましては、我々はあえて両方向性に転写が起きている領域のみに注目していることで、より機能的なエンハンサー領域に絞られていることかと思います。デメリットとしては、リファレンスにGがあるとどうしても過度にリードをfilteringすることになり、promoter領域の発現値は低く見積もっている可能性がある、ことと思います。
- Q14: バルクRNA-seqで転写開始点解析を実施してそこまで良い思い出はないのですが、シングルセルになることで精度や情報量に違いはありそうですか？
  - A14: ご質問有難うございます。Bulk RNA-seq (CAGE?)で必要とされていたRNA量よりもはるかに少ない量でエンハンサー解析ができ、シングルセルとして細胞ごと、クラスターごとの解析ができるだけでなく、bulk扱いでの解析もできますので、情報量ははるかに多いと思います。精度という意味では、同じくらい（CAGE法はそもそもcap trapper法を使っているので、精度が良いが、ReapTEC法を利用するとさらに精度が増す）かと思います。
