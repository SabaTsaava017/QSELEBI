# QSELEBI
1.მოცემულია კონვოლუციის შრეში შემავალი მატრიცა a და ფილტრი w. გამოითვალეთ ფილტრის გადავლის შემდეგ დაბრუნებული მატრიცის მნიშვნელობები, თუ padding = 1,
stride = 1 და b = 0.

a = [[2, 0, 1, 0]          w = [[0, 1, 1]
     [0, 1, 0, 1]               [-1, 0, -1]
     [1, 2, 0, 1]               [0,-1, 1]] 
     [0, 2, 2, 1]] 



შედეგი:

[1  1  -1  1]
[2  -1  0  0]
[ 2  1  2  0]
[1  1  3  1  ]

2.აღწერეთ რეკურენტული ნეირონი, შეადარეთ ის სტანდარტული ნეირონისი აგებულებას და განმარტეთ რა სხვაობაა მათ შორის.ასევე ისაუბრეთ RNN - ის შეზღუდვებზე, რა პრობლემას შეიძლება  გადავაწყდეთ მისი გამოყენებისას და რა გზები არსებობს ამ პრობლემების თავიდან ასარიდებლად. 

სტანდარტული ნეირონი (Feedforward Neuron):
სტანდარტული ნეირონი, რომელიც გვხვდება ჩვეულებრივ ნეირონულ ქსელებში (მაგ., MLP - Multilayer Perceptron), იღებს გარკვეულ რაოდენობის შეყვანებს (input), ამუშავებს მათ წონების (weights) და აქტივაციის ფუნქციის საშუალებით, შემდეგ კი გამოსცემს ერთჯერად შედეგს. ეს ნეირონი მუშაობს ერთი მიმართულებით – შეყვანიდან გამოსავლისკენ, რაც ნიშნავს, რომ მას არ გააჩნია მეხსიერება და ვერ ამუშავებს დროით დამოკიდებულ მონაცემებს.

რეკურენტული ნეირონი (Recurrent Neuron):
რეკურენტული ნეირონი მუშაობს განსხვავებული პრინციპით – მას აქვს შიდა უკუკავშირი, რაც ნიშნავს, რომ ის არა მხოლოდ მიმდინარე შეყვანას ამუშავებს, არამედ ინახავს წინა მდგომარეობის (hidden state) ინფორმაციას. ეს მეხსიერების მექანიზმი საშუალებას აძლევს რეკურენტულ ნეირონულ ქსელებს (RNN - Recurrent Neural Networks) დაამუშაონ დროითი სერიები და სხვა მიმდევრობითი მონაცემები.


შედარება:

სტანდარტული ნეირონი და რეკურენტული ნეირონი ერთმანეთისგან მნიშვნელოვნად განსხვავდებიან.

სტანდარტული ნეირონი იღებს გარკვეულ შეყვანას, ამუშავებს მას წონებისა და აქტივაციის ფუნქციის საშუალებით და იძლევა გამოსავალს, რომელიც დამოკიდებულია მხოლოდ ამ კონკრეტულ შეყვანაზე. ის არ ინახავს წინა მდგომარეობას და ვერ ამუშავებს მიმდევრობით მონაცემებს. ამიტომ, იგი გამოიყენება ისეთ ამოცანებში, სადაც მონაცემებს შორის დროითი ან მიმდევრობითი კავშირი არ არის აუცილებელი, მაგალითად, სურათების ან სტატიკური მონაცემების კლასიფიკაციაში.

რეკურენტული ნეირონი, თავის მხრივ, შიდა უკუკავშირის მექანიზმის გამო ინარჩუნებს წინა მდგომარეობის ინფორმაციას და მასთან ერთად ამუშავებს ახალ შეყვანას. ეს მახასიათებელი მას განსაკუთრებით გამოსადეგს ხდის დროით დამოკიდებული მონაცემებისთვის, როგორიცაა ტექსტი, აუდიო, ვიდეო ან დროითი სერიები.

მთავარი განსხვავება მათ შორის ის არის, რომ სტანდარტული ნეირონი თითოეულ შეყვანას დამოუკიდებლად ამუშავებს, მაშინ როცა რეკურენტული ნეირონი ეყრდნობა წინა მდგომარეობის შედეგს, რაც აძლევს მას "მეხსიერების" შესაძლებლობას. შესაბამისად, RNN იდეალურია ტექსტის გენერირებისთვის, მეტყველების ამოცნობისთვის და სხვა მსგავსი ამოცანებისთვის, სადაც წინა კონტექსტის გათვალისწინება აუცილებელია.



RNN-ის შეზღუდვები და გამოწვევები
გრძელი მიმდევრობითი მონაცემების დამუშავება

RNN-ები კარგია მოკლე მიმდევრობებისთვის, მაგრამ გრძელი მიმდევრობითი მონაცემების დამუშავებისას გაქრობის გრადიენტის (Vanishing Gradient) პრობლემა იჩენს თავს. ეს ნიშნავს, რომ ქსელი ვერ ინარჩუნებს შორეულ წარსულში არსებულ ინფორმაციას, რადგან გრადიენტები ტრენინგისას საგრძნობლად მცირდება.
გარდაუვალი გრადიენტის (Exploding Gradient) პრობლემა – ზოგჯერ გრადიენტები პირიქით, ძალიან იზრდება და ტრენინგი დესტაბილურდება.
პარალელიზაციის ნაკლებობა

სტანდარტული ნეირონული ქსელებისგან განსხვავებით, RNN-ები მუშაობენ მიმდევრობით (სერიული პროცესირება), რაც ამცირებს მათ პარალელიზაციის შესაძლებლობას და ანელებს ტრენინგს.
გრძელი დამოკიდებულებების დამუშავების სირთულე

მიუხედავად იმისა, რომ RNN-ს შეუძლია წარსულის ინფორმაციის შენახვა, ის ხშირად ვერ უმკლავდება გრძელვადიან დამოკიდებულებებს.
როგორ დავძლიოთ ეს შეზღუდვები?
LSTM (Long Short-Term Memory) და GRU (Gated Recurrent Unit)

LSTM-ები და GRU-ები სპეციალურად შექმნილია RNN-ების პრობლემების გადასაჭრელად.
LSTM-ები იყენებენ სპეციალურ "კარებს" (Gates), რომლებიც არეგულირებენ, რა ინფორმაცია უნდა დარჩეს და რა უნდა დაივიწყოს.
GRU მუშაობს მსგავსად, მაგრამ უფრო მარტივი სტრუქტურა აქვს და ნაკლებ გამოთვლით რესურსს მოითხოვს.
Gradient Clipping

თუ გრადიენტი ზედმეტად იზრდება (Exploding Gradient), მისი გარკვეული ზღვრის მიღმა შეზღუდვა (Clipping) შესაძლებელია.
Attention Mechanism და Transformer-ები

Attention მექანიზმი უკეთესად ახერხებს გრძელი დამოკიდებულებების დამუშავებას.
Transformer არქიტექტურამ (მაგ., BERT, GPT) ფაქტობრივად ჩაანაცვლა RNN-ები ბუნებრივი ენის დამუშავებაში (NLP), რადგან ის საშუალებას იძლევა ერთდროულად დამუშავდეს მთელი მიმდევრობა, ნაცვლად სერიული გამოთვლების.
Bidirectional RNN

სტანდარტული RNN ინფორმაციის დამუშავებას მხოლოდ ერთი მიმართულებით ახდენს (წარსულიდან მომავალში). Bidirectional RNN იყენებს ორივე მიმართულებას, რაც აუმჯობესებს შედეგებს.
დასკვნა
მიუხედავად იმისა, რომ RNN-ებს აქვთ მნიშვნელოვანი შეზღუდვები, მათი გაუმჯობესებული ვარიანტები, როგორიცაა LSTM და GRU, და ახალი მოდელები, როგორიცაა Transformer, შესაძლებელს ხდის უფრო ეფექტურად დამუშავდეს დროით დამოკიდებული მონაცემები. RNN-ები ჯერ კიდევ სასარგებლოა ისეთ დავალებებში, სადაც მნიშვნელოვანია მიმდევრობითი დამუშავება, მაგრამ თანამედროვე ნეირონული ქსელების განვითარებასთან ერთად, ისინი ბევრ სფეროში ნაკლებად გამოიყენება.




მოკლე ვერსია:


რეკურენტული ნეირონი არის ნეირონი, რომელსაც აქვს შიდა უკუკავშირი, რაც საშუალებას აძლევს შეინარჩუნოს და გამოიყენოს წინა დროითი მომენტების ინფორმაცია. ეს თვისება მას იდეალურად აქცევს მიმდევრობითი მონაცემების, როგორიცაა ტექსტი, ხმა და დროითი სერიები, დამუშავებისთვის.

შედარება სტანდარტულ ნეირონთან:

სტანდარტული ნეირონი იღებს შეყვანას, მას ამუშავებს და შედეგს გამოიტანს უშუალოდ, ყოველგვარი მეხსიერების გარეშე.
რეკურენტული ნეირონი ინახავს წინა მდგომარეობას და ახალ შეყვანასთან ერთად მას კვლავ ამუშავებს, რაც შესაძლებელს ხდის კონტექსტზე დაფუძნებული შედეგების მიღებას.
RNN-ის შეზღუდვები:

გაქრობის გრადიენტის პრობლემა – გრძელვადიანი დამოკიდებულებების დამუშავება რთულია, რადგან გრადიენტები ტრენინგისას მცირდება.
პარალელიზაციის ნაკლებობა – გამომდინარე სერიული დამუშავებიდან, ტრენინგი უფრო ნელია.
გრძელი დამოკიდებულებების დამუშავების სირთულე – შორეული კონტექსტის შენარჩუნება ცუდად ხერხდება.

ამ პრობლემების გადაჭრის გზები:
LSTM და GRU – გაუმჯობესებული არქიტექტურები, რომლებიც უკეთ ინახავენ შორეულ ინფორმაციას.
Gradient Clipping – გრადიენტების კონტროლი, რომ ტრენინგი სტაბილური იყოს.
Attention Mechanism და Transformers – თანამედროვე მიდგომები, რომლებიც უკეთესად უმკლავდებიან გრძელდისტანციურ დამოკიდებულებებს.
Bidirectional RNN – ინფორმაციის დამუშავება ორივე მიმართულებით კონტექსტის უკეთ გასაანალიზებლად.




3. აღწერეთ მოცემული ტრანსფორმერის არქიტექტურა.
განიხილეთ ენკოდერისა და დეკოდერის ბლოკების შიდა სტრუქტურა, შეადარეთ ის RNN-ს და ახსენით რა უპირატესობა აქვს ტრანსფორმერის არქიტეტურას მასთან შედარებით.

ენკოდერი (Encoder) – მარცხენა მხარეს
დეკოდერი (Decoder) – მარჯვენა მხარეს

ენკოდერი
ენკოდერი შედგება მრავალი (N) იდენტური ბლოკისგან. თითოეული ბლოკი შეიცავს შემდეგ კომპონენტებს:

მრავალთავიანი ყურადღება (Multi-Head Attention) – უზრუნველყოფს შეყვანილი ინფორმაციის დამუშავებას პარალელურად, ეხმარება სხვადასხვა დამოკიდებულებების შესწავლაში.
ნორმალიზაცია და დანამატი (Add & Norm) – მოიცავს ნაშთოვან კავშირს (Residual Connection) და ლეიერის ნორმალიზაციას (Layer Normalization), რაც მოდელს სტაბილურობას სძენს.
წინ გადაცემული (Feed Forward) ფენა – ყოველი კოდის ბლოკი შეიცავს ცალკეულ, დამოუკიდებელ, სრულად დაკავშირებულ ნეირონულ ქსელს.
პოზიციური კოდირება (Positional Encoding) – ტრანსფორმერი არ არის რიგითობის (Sequential) დაფუძნებული მოდელი, ამიტომ თითოეულ ტოკენს უნიკალური პოზიციური ინფორმაცია ემატება.

დეკოდერი
დეკოდერი ასევე შედგება N ბლოკისგან და შეიცავს:

ნიღბიანი მრავალთავიანი ყურადღება (Masked Multi-Head Attention) – ნიღბვის (Masking) მეშვეობით გარანტირებულია, რომ მოდელმა არ დაინახოს მომავალი სიტყვები თარჯიმნის პროცესში.
მრავალთავიანი ყურადღება (Multi-Head Attention) – ეს ბლოკი აკავშირებს დეკოდერს ენკოდერის გამომუშავებულ წარმომადგენლობებთან.
წინ გადაცემული ფენა (Feed Forward Layer) – როგორც ენკოდერში, ასევე დეკოდერში არის დამოუკიდებელი სრულად დაკავშირებული ფენა.
Softmax და Linear ფენები – საბოლოოდ, მოდელი გამოითვლის ყოველი ტოკენის ალბათობას სიტყვების სავარაუდო შედეგებისთვის.


შედარება RNN-თან
ტრადიციულ რეკურენტულ ნეირონულ ქსელებთან (RNNs) შედარებით, ტრანსფორმერს რამდენიმე უპირატესობა აქვს:


ტრანსფორმერი                                                                                                                                                     RNN

პარალელიზაცია – ყველა ტოკენი ერთდროულად მუშავდება	                                                                სეკვენციური დამუშავება – ტოკენები დამუშავდება ერთმანეთის მიყოლებით
დიდი კონტექსტის დანახვა – შეუძლია გრძელდისტანციური დამოკიდებულებების სწავლა	გარკვეული კონტექსტის დაკარგვა – უჭირს შორეულ სიტყვებს შორის კავშირების სწავლა
მრავალთავიანი ყურადღება – სხვადასხვა დონეზე ამუშავებს სიტყვებს	                                                ვექტორიზებული დამუშავება – ყველა სიტყვა ერთნაირად აღიქმება
არ აქვს ვანიშინგ გრადიანტის პრობლემა	                                                                                                 დამოკიდებულია LSTM/GRU-ს ხსოვნაზე


დასკვნა
ტრანსფორმერის არქიტექტურა ეფექტურია დიდი მოცულობის ტექსტის გადამუშავებისთვის, რადგან იგი აერთიანებს პარალელურ დამუშავებას, შორსმიმავალი დამოკიდებულებების სწავლას და სტაბილურ ოპტიმიზაციას. სწორედ ამიტომ, ეს არქიტექტურა ფართოდ გამოიყენება თანამედროვე ნეირონული მანქანური თარგმნის, ტექსტის გენერაციისა და სხვა NLP ამოცანებში.

