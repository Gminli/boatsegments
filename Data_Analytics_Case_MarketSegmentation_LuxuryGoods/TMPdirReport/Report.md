<link rel="stylesheet" href="http://netdna.bootstrapcdn.com/bootstrap/3.0.3/css/bootstrap.min.css">
<style type="text/css"> body {padding: 10px 30px 10px 30px;} table,th, td {text-align: center;}</style>
<style>
td.tableRow
{
text-align:center;
}
</style>


Customer Segmentation in the Boating Industry
========================================================

**J. Niessing, INSEAD**

**T. Evgeniou, INSEAD**


The Business Issue
---------------------------------------------------------

A boating company had become a victim of the crisis in the boating industry. The business problem of the "Boat" case study, although hypothetical, depicts very well the sort of business problems faced by many real companies in an increasingly data-intensive business environment. The management team was now exploring various growth options. Expanding further in some markets, in particular North America, was no longer something to consider for the distant future. It was becoming an immediate necessity. 

The team believed that in order to develop a strategy for North America, they needed a better understanding of their current and potential customers in that market. They believed that they had to build more targeted boats for their most important segments there. To that purpose, the boating company had been commissioned a segmentation project for that market. Being a data-friendly company, the decision was made to develop a segmentation in a data-driven way - none of that soft hold-hands-and-discuss stuff. 


The Data
--------------------------------------------

With the aid of a market research firm, the boating company gathered various data about the boating market in the US through interviews with almost 3,000 boat owners and intenders. The data consisted, among others, 29 attitudes towards boating, which respondents indicated on a 5-point scale (Q. 1, 1-29 shown in the survey in the appendix).

Other types of information had been collected, such as demographics (Q. 11-15 in the survey). Finally, the boating company had compiled information about the boats, such as the length of the boat they owned, how they used their boats, and the price of the boats (Q. 2-10 in the survey). A segmentation and profile of the market would be done using all this data. 

The Approach
--------------------------------------------

Based on past experience, the decision was made to develop a segmentation that was mostly driven by attitudes that consumer held regarding boating - the attitudinal data from the 29 questions in Q.1.

### Factor Analysis

As a first step, the company decided to simplify the data by grouping the 29 attitudinal statements in Q1 into a few meaningful sets/factors. This could be done using a standard method: factor analysis. The objective is to summarize information (the variation) in correlated raw attributes to a smaller number of manageable factors - which are typically uncorrelated or independent. In the process one decreases the number of raw attributes while keeping most of the information in the data in a statistical sense. This data reduction technique is a very useful step in helping interpreting the data and make better decisions. It also helps to identify the key variables that should be used in the segmentation procedure. 

We first have to read the whole dataset, which is in CSV format.

For the Factor Analysis, we will only use the 29 items of the data that describe the attitudes towards boating of people in the sample. Such 29 items are measured on a Likert scale of 1-5. All the 29 items are integer variables that take values between 1 (=strongly disagree) and 5 (=strongly agree).

Every factor analysis has three basic decision points:  

- Decide the number of factors, 

- Choose an extraction method, 

- Choose a rotation method.  


Sometimes it makes sense to run a quick correlation matrix before the factor analysis. It usually gives a first glance at the inter-relationships between variables and it is often an input for factor analysis (i.e. eigenvalue decomposition of the correlation matrix). In this example the correlaton matrix for the 29 attitudes looks like this: 

<style>
.wrapper{


width: 100%;

overflow-x: scroll;

}
.wrapper1{

height:400px;
overflow-y: scroll;
}
th.wrapper{
display:block;
}

</style>




<div class="wrapper wrapper1 th.display">

<table border="1" class="data table table-bordered table-condensed">
  <thead class="thead" style="font-size:10px;">
    <tr>
      <th style="position:fixed;"></th>
      <th>Q1_1_When buying a boat  I do a lot of shopping around and visit multiple dealers</th>
      <th>Q1_2_When buying a boat  getting the lowest price is more important than the boat brand</th>
      <th>Q1_3_The brand of boat I buy says a lot about who I am</th>
      <th>Q1_4_I only consider buying a boat from a reputable brand</th>
      <th>Q1_5_I am willing to pay a premium for a brand with a reputation for high quality</th>
      <th>Q1_6_Owning a boat is a way of rewarding myself for my hard work</th>
      <th>Q1_7_Owning a boat gives me a sense of achievement</th>
      <th>Q1_8_When buying a boat  functionality is more important than style</th>
      <th>Q1_9_I see my boat as a status symbol</th>
      <th>Q1_10_When buying a boat  I rely more on expert opinion than my own  e g  consumer reports  salespeople </th>
      <th>Q1_11_I tend to perform minor boat repairs and maintenance on my own</th>
      <th>Q1_12_When it comes to boating  I tend to prefer a basic boat with little to no frills</th>
      <th>Q1_13_When buying a boat  I tend to buy the latest and greatest</th>
      <th>Q1_14_When buying accessories for my boat  I tend to buy the latest and greatest</th>
      <th>Q1_15_I am serious about the technology on my boat</th>
      <th>Q1_16_People tend to come to me for advice about boating</th>
      <th>Q1_17_I consider myself more knowledgeable about boating than the rest of my boating peers</th>
      <th>Q1_18_Boating gives me a feeling of adventure</th>
      <th>Q1_19_Boating allows me to experience nature</th>
      <th>Q1_20_When not on my boat  I often find myself doing boating related activities</th>
      <th>Q1_21_Boating helps me escape from everyday life and relax</th>
      <th>Q1_22_Boating helps me stay active</th>
      <th>Q1_23_Boating allows me to excel in the sports that I am passionate about   e g  fishing  racing  water sports </th>
      <th>Q1_24_Boating gives me an outlet to socialize with family and or friends</th>
      <th>Q1_25_Being in charge of my boat is very important to me</th>
      <th>Q1_26_Having a powerful boat is what is most important to me</th>
      <th>Q1_27_Boating is the number one thing I do with my spare time</th>
      <th>Q1_28_Boating is my true passion in life</th>
      <th>Q1_29_Boating is one of many things I do in my spare time</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td align="center" style="font-size:10px;">Q1_1_When buying a boat  I do a lot of shopping around and visit multiple dealers</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(253,255,253)">0.008983336</td>
      <td align="right" style="background-color: rgb(228,255,228)">0.1074657</td>
      <td align="right" style="background-color: rgb(205,255,205)">0.1982769</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1835384</td>
      <td align="right" style="background-color: rgb(187,255,187)">0.2677592</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1846069</td>
      <td align="right" style="background-color: rgb(233,255,233)">0.08861377</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07780153</td>
      <td align="right" style="background-color: rgb(228,255,228)">0.1071152</td>
      <td align="right" style="background-color: rgb(218,255,218)">0.1448968</td>
      <td align="right" style="background-color: rgb(255,242,242)">-0.05305449</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1225231</td>
      <td align="right" style="background-color: rgb(210,255,210)">0.1785</td>
      <td align="right" style="background-color: rgb(189,255,189)">0.2610791</td>
      <td align="right" style="background-color: rgb(215,255,215)">0.1571813</td>
      <td align="right" style="background-color: rgb(218,255,218)">0.1478382</td>
      <td align="right" style="background-color: rgb(191,255,191)">0.2532779</td>
      <td align="right" style="background-color: rgb(185,255,185)">0.2739737</td>
      <td align="right" style="background-color: rgb(206,255,206)">0.1941126</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2352835</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2314947</td>
      <td align="right" style="background-color: rgb(207,255,207)">0.1875854</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2091071</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2270835</td>
      <td align="right" style="background-color: rgb(229,255,229)">0.1037838</td>
      <td align="right" style="background-color: rgb(223,255,223)">0.1268492</td>
      <td align="right" style="background-color: rgb(210,255,210)">0.1760324</td>
      <td align="right" style="background-color: rgb(204,255,204)">0.2016025</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_2_When buying a boat  getting the lowest price is more important than the boat brand</td>
      <td align="right" style="background-color: rgb(253,255,253)">0.008983336</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.0295586</td>
      <td align="right" style="background-color: rgb(255,202,202)">-0.2101034</td>
      <td align="right" style="background-color: rgb(255,203,203)">-0.2058222</td>
      <td align="right" style="background-color: rgb(255,246,246)">-0.03726964</td>
      <td align="right" style="background-color: rgb(250,255,250)">0.02025272</td>
      <td align="right" style="background-color: rgb(205,255,205)">0.196743</td>
      <td align="right" style="background-color: rgb(233,255,233)">0.08721974</td>
      <td align="right" style="background-color: rgb(215,255,215)">0.1582789</td>
      <td align="right" style="background-color: rgb(245,255,245)">0.04284929</td>
      <td align="right" style="background-color: rgb(161,255,161)">0.3702303</td>
      <td align="right" style="background-color: rgb(254,255,254)">0.006216449</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.03047899</td>
      <td align="right" style="background-color: rgb(255,236,236)">-0.07768844</td>
      <td align="right" style="background-color: rgb(255,252,252)">-0.01528283</td>
      <td align="right" style="background-color: rgb(246,255,246)">0.03891559</td>
      <td align="right" style="background-color: rgb(255,246,246)">-0.0377051</td>
      <td align="right" style="background-color: rgb(255,246,246)">-0.03631476</td>
      <td align="right" style="background-color: rgb(242,255,242)">0.05335306</td>
      <td align="right" style="background-color: rgb(255,230,230)">-0.09945353</td>
      <td align="right" style="background-color: rgb(255,236,236)">-0.07644686</td>
      <td align="right" style="background-color: rgb(255,255,255)">0.002846742</td>
      <td align="right" style="background-color: rgb(255,236,236)">-0.07550207</td>
      <td align="right" style="background-color: rgb(253,255,253)">0.008885516</td>
      <td align="right" style="background-color: rgb(237,255,237)">0.0737951</td>
      <td align="right" style="background-color: rgb(244,255,244)">0.04546034</td>
      <td align="right" style="background-color: rgb(251,255,251)">0.01601573</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.02895487</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_3_The brand of boat I buy says a lot about who I am</td>
      <td align="right" style="background-color: rgb(228,255,228)">0.1074657</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.0295586</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(188,255,188)">0.2636314</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.3996899</td>
      <td align="right" style="background-color: rgb(168,255,168)">0.3400978</td>
      <td align="right" style="background-color: rgb(142,255,142)">0.443638</td>
      <td align="right" style="background-color: rgb(255,242,242)">-0.05102428</td>
      <td align="right" style="background-color: rgb(107,255,107)">0.578913</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.1356028</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09649344</td>
      <td align="right" style="background-color: rgb(255,233,233)">-0.08892755</td>
      <td align="right" style="background-color: rgb(131,255,131)">0.4845101</td>
      <td align="right" style="background-color: rgb(137,255,137)">0.4615334</td>
      <td align="right" style="background-color: rgb(159,255,159)">0.3762223</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.3871884</td>
      <td align="right" style="background-color: rgb(158,255,158)">0.3790491</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2379419</td>
      <td align="right" style="background-color: rgb(219,255,219)">0.1413975</td>
      <td align="right" style="background-color: rgb(157,255,157)">0.3855504</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1819674</td>
      <td align="right" style="background-color: rgb(183,255,183)">0.281364</td>
      <td align="right" style="background-color: rgb(169,255,169)">0.3395666</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2276743</td>
      <td align="right" style="background-color: rgb(164,255,164)">0.3580322</td>
      <td align="right" style="background-color: rgb(135,255,135)">0.4710066</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.4008411</td>
      <td align="right" style="background-color: rgb(147,255,147)">0.4252522</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1659069</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_4_I only consider buying a boat from a reputable brand</td>
      <td align="right" style="background-color: rgb(205,255,205)">0.1982769</td>
      <td align="right" style="background-color: rgb(255,202,202)">-0.2101034</td>
      <td align="right" style="background-color: rgb(188,255,188)">0.2636314</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3666674</td>
      <td align="right" style="background-color: rgb(204,255,204)">0.2015499</td>
      <td align="right" style="background-color: rgb(211,255,211)">0.1753396</td>
      <td align="right" style="background-color: rgb(255,255,255)">0.003763867</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1676266</td>
      <td align="right" style="background-color: rgb(230,255,230)">0.1000801</td>
      <td align="right" style="background-color: rgb(240,255,240)">0.05880257</td>
      <td align="right" style="background-color: rgb(255,215,215)">-0.1598127</td>
      <td align="right" style="background-color: rgb(186,255,186)">0.2726845</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2941087</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2961264</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1820797</td>
      <td align="right" style="background-color: rgb(211,255,211)">0.1748554</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1845094</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1854829</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1832706</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1830434</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2335025</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1642283</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2291016</td>
      <td align="right" style="background-color: rgb(200,255,200)">0.2180119</td>
      <td align="right" style="background-color: rgb(206,255,206)">0.1922681</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1650017</td>
      <td align="right" style="background-color: rgb(201,255,201)">0.2124064</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1865064</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_5_I am willing to pay a premium for a brand with a reputation for high quality</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1835384</td>
      <td align="right" style="background-color: rgb(255,203,203)">-0.2058222</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.3996899</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3666674</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(181,255,181)">0.2929145</td>
      <td align="right" style="background-color: rgb(182,255,182)">0.2854438</td>
      <td align="right" style="background-color: rgb(255,247,247)">-0.03321855</td>
      <td align="right" style="background-color: rgb(171,255,171)">0.3286888</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.135732</td>
      <td align="right" style="background-color: rgb(238,255,238)">0.06922647</td>
      <td align="right" style="background-color: rgb(255,211,211)">-0.172454</td>
      <td align="right" style="background-color: rgb(140,255,140)">0.4503552</td>
      <td align="right" style="background-color: rgb(138,255,138)">0.4599086</td>
      <td align="right" style="background-color: rgb(149,255,149)">0.4176032</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3552757</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3183953</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2341611</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1842438</td>
      <td align="right" style="background-color: rgb(173,255,173)">0.322899</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1872704</td>
      <td align="right" style="background-color: rgb(185,255,185)">0.2737216</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2934292</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.249245</td>
      <td align="right" style="background-color: rgb(181,255,181)">0.2902679</td>
      <td align="right" style="background-color: rgb(169,255,169)">0.3372278</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2940066</td>
      <td align="right" style="background-color: rgb(172,255,172)">0.3250107</td>
      <td align="right" style="background-color: rgb(210,255,210)">0.1778252</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_6_Owning a boat is a way of rewarding myself for my hard work</td>
      <td align="right" style="background-color: rgb(187,255,187)">0.2677592</td>
      <td align="right" style="background-color: rgb(255,246,246)">-0.03726964</td>
      <td align="right" style="background-color: rgb(168,255,168)">0.3400978</td>
      <td align="right" style="background-color: rgb(204,255,204)">0.2015499</td>
      <td align="right" style="background-color: rgb(181,255,181)">0.2929145</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(116,255,116)">0.5459713</td>
      <td align="right" style="background-color: rgb(245,255,245)">0.04035715</td>
      <td align="right" style="background-color: rgb(166,255,166)">0.3489418</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1245463</td>
      <td align="right" style="background-color: rgb(218,255,218)">0.1461497</td>
      <td align="right" style="background-color: rgb(255,226,226)">-0.1154492</td>
      <td align="right" style="background-color: rgb(182,255,182)">0.2856959</td>
      <td align="right" style="background-color: rgb(175,255,175)">0.3137982</td>
      <td align="right" style="background-color: rgb(175,255,175)">0.314295</td>
      <td align="right" style="background-color: rgb(186,255,186)">0.2717595</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2361925</td>
      <td align="right" style="background-color: rgb(143,255,143)">0.4375378</td>
      <td align="right" style="background-color: rgb(164,255,164)">0.35552</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3540081</td>
      <td align="right" style="background-color: rgb(147,255,147)">0.4242353</td>
      <td align="right" style="background-color: rgb(151,255,151)">0.4088023</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3179028</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.366991</td>
      <td align="right" style="background-color: rgb(148,255,148)">0.4200361</td>
      <td align="right" style="background-color: rgb(177,255,177)">0.3073585</td>
      <td align="right" style="background-color: rgb(167,255,167)">0.3446675</td>
      <td align="right" style="background-color: rgb(155,255,155)">0.3924007</td>
      <td align="right" style="background-color: rgb(186,255,186)">0.2714557</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_7_Owning a boat gives me a sense of achievement</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1846069</td>
      <td align="right" style="background-color: rgb(250,255,250)">0.02025272</td>
      <td align="right" style="background-color: rgb(142,255,142)">0.443638</td>
      <td align="right" style="background-color: rgb(211,255,211)">0.1753396</td>
      <td align="right" style="background-color: rgb(182,255,182)">0.2854438</td>
      <td align="right" style="background-color: rgb(116,255,116)">0.5459713</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(255,254,254)">-0.005650749</td>
      <td align="right" style="background-color: rgb(130,255,130)">0.4907995</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1216784</td>
      <td align="right" style="background-color: rgb(226,255,226)">0.1151871</td>
      <td align="right" style="background-color: rgb(255,228,228)">-0.109083</td>
      <td align="right" style="background-color: rgb(166,255,166)">0.3489323</td>
      <td align="right" style="background-color: rgb(163,255,163)">0.3619325</td>
      <td align="right" style="background-color: rgb(167,255,167)">0.3448759</td>
      <td align="right" style="background-color: rgb(176,255,176)">0.309052</td>
      <td align="right" style="background-color: rgb(182,255,182)">0.2852205</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.4009004</td>
      <td align="right" style="background-color: rgb(183,255,183)">0.2815365</td>
      <td align="right" style="background-color: rgb(163,255,163)">0.363264</td>
      <td align="right" style="background-color: rgb(172,255,172)">0.3273714</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.3901573</td>
      <td align="right" style="background-color: rgb(178,255,178)">0.3044174</td>
      <td align="right" style="background-color: rgb(170,255,170)">0.3327883</td>
      <td align="right" style="background-color: rgb(148,255,148)">0.4194157</td>
      <td align="right" style="background-color: rgb(157,255,157)">0.3864856</td>
      <td align="right" style="background-color: rgb(161,255,161)">0.370631</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.3993589</td>
      <td align="right" style="background-color: rgb(194,255,194)">0.2405801</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_8_When buying a boat  functionality is more important than style</td>
      <td align="right" style="background-color: rgb(233,255,233)">0.08861377</td>
      <td align="right" style="background-color: rgb(205,255,205)">0.196743</td>
      <td align="right" style="background-color: rgb(255,242,242)">-0.05102428</td>
      <td align="right" style="background-color: rgb(255,255,255)">0.003763867</td>
      <td align="right" style="background-color: rgb(255,247,247)">-0.03321855</td>
      <td align="right" style="background-color: rgb(245,255,245)">0.04035715</td>
      <td align="right" style="background-color: rgb(255,254,254)">-0.005650749</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(255,232,232)">-0.09187996</td>
      <td align="right" style="background-color: rgb(234,255,234)">0.08512243</td>
      <td align="right" style="background-color: rgb(219,255,219)">0.142578</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2353861</td>
      <td align="right" style="background-color: rgb(255,243,243)">-0.04788385</td>
      <td align="right" style="background-color: rgb(255,250,250)">-0.02173115</td>
      <td align="right" style="background-color: rgb(240,255,240)">0.06131853</td>
      <td align="right" style="background-color: rgb(250,255,250)">0.02284145</td>
      <td align="right" style="background-color: rgb(243,255,243)">0.04813343</td>
      <td align="right" style="background-color: rgb(237,255,237)">0.07380629</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09497647</td>
      <td align="right" style="background-color: rgb(244,255,244)">0.04331111</td>
      <td align="right" style="background-color: rgb(239,255,239)">0.06314187</td>
      <td align="right" style="background-color: rgb(242,255,242)">0.05411788</td>
      <td align="right" style="background-color: rgb(230,255,230)">0.09931021</td>
      <td align="right" style="background-color: rgb(251,255,251)">0.01860354</td>
      <td align="right" style="background-color: rgb(230,255,230)">0.09905621</td>
      <td align="right" style="background-color: rgb(255,244,244)">-0.04453738</td>
      <td align="right" style="background-color: rgb(248,255,248)">0.02919826</td>
      <td align="right" style="background-color: rgb(244,255,244)">0.04578701</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09731618</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_9_I see my boat as a status symbol</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07780153</td>
      <td align="right" style="background-color: rgb(233,255,233)">0.08721974</td>
      <td align="right" style="background-color: rgb(107,255,107)">0.578913</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1676266</td>
      <td align="right" style="background-color: rgb(171,255,171)">0.3286888</td>
      <td align="right" style="background-color: rgb(166,255,166)">0.3489418</td>
      <td align="right" style="background-color: rgb(130,255,130)">0.4907995</td>
      <td align="right" style="background-color: rgb(255,232,232)">-0.09187996</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(219,255,219)">0.1430428</td>
      <td align="right" style="background-color: rgb(240,255,240)">0.05986664</td>
      <td align="right" style="background-color: rgb(255,244,244)">-0.04385902</td>
      <td align="right" style="background-color: rgb(133,255,133)">0.4801163</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4267455</td>
      <td align="right" style="background-color: rgb(170,255,170)">0.3327023</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.389195</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3656044</td>
      <td align="right" style="background-color: rgb(200,255,200)">0.218012</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07439851</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3659377</td>
      <td align="right" style="background-color: rgb(219,255,219)">0.1435208</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.232465</td>
      <td align="right" style="background-color: rgb(182,255,182)">0.2886866</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2304275</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3190602</td>
      <td align="right" style="background-color: rgb(127,255,127)">0.5026779</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.3996665</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.40248</td>
      <td align="right" style="background-color: rgb(226,255,226)">0.1146627</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_10_When buying a boat  I rely more on expert opinion than my own  e g  consumer reports  salespeople </td>
      <td align="right" style="background-color: rgb(228,255,228)">0.1071152</td>
      <td align="right" style="background-color: rgb(215,255,215)">0.1582789</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.1356028</td>
      <td align="right" style="background-color: rgb(230,255,230)">0.1000801</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.135732</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1245463</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1216784</td>
      <td align="right" style="background-color: rgb(234,255,234)">0.08512243</td>
      <td align="right" style="background-color: rgb(219,255,219)">0.1430428</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(255,233,233)">-0.08855422</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1223091</td>
      <td align="right" style="background-color: rgb(214,255,214)">0.1614156</td>
      <td align="right" style="background-color: rgb(229,255,229)">0.1051007</td>
      <td align="right" style="background-color: rgb(227,255,227)">0.1111225</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.03011578</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.02844251</td>
      <td align="right" style="background-color: rgb(220,255,220)">0.1406122</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09458814</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09627565</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07687198</td>
      <td align="right" style="background-color: rgb(232,255,232)">0.09113168</td>
      <td align="right" style="background-color: rgb(238,255,238)">0.06954759</td>
      <td align="right" style="background-color: rgb(222,255,222)">0.131241</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07601007</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.1348247</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07710982</td>
      <td align="right" style="background-color: rgb(238,255,238)">0.06921813</td>
      <td align="right" style="background-color: rgb(242,255,242)">0.05107339</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_11_I tend to perform minor boat repairs and maintenance on my own</td>
      <td align="right" style="background-color: rgb(218,255,218)">0.1448968</td>
      <td align="right" style="background-color: rgb(245,255,245)">0.04284929</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09649344</td>
      <td align="right" style="background-color: rgb(240,255,240)">0.05880257</td>
      <td align="right" style="background-color: rgb(238,255,238)">0.06922647</td>
      <td align="right" style="background-color: rgb(218,255,218)">0.1461497</td>
      <td align="right" style="background-color: rgb(226,255,226)">0.1151871</td>
      <td align="right" style="background-color: rgb(219,255,219)">0.142578</td>
      <td align="right" style="background-color: rgb(240,255,240)">0.05986664</td>
      <td align="right" style="background-color: rgb(255,233,233)">-0.08855422</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(233,255,233)">0.08747504</td>
      <td align="right" style="background-color: rgb(235,255,235)">0.07991006</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.1345263</td>
      <td align="right" style="background-color: rgb(203,255,203)">0.2049692</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3192129</td>
      <td align="right" style="background-color: rgb(177,255,177)">0.3079996</td>
      <td align="right" style="background-color: rgb(227,255,227)">0.1119335</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1233462</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2499986</td>
      <td align="right" style="background-color: rgb(222,255,222)">0.1291384</td>
      <td align="right" style="background-color: rgb(212,255,212)">0.1700732</td>
      <td align="right" style="background-color: rgb(206,255,206)">0.1920789</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07730115</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2488671</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09385587</td>
      <td align="right" style="background-color: rgb(215,255,215)">0.1570309</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1829313</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1659397</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_12_When it comes to boating  I tend to prefer a basic boat with little to no frills</td>
      <td align="right" style="background-color: rgb(255,242,242)">-0.05305449</td>
      <td align="right" style="background-color: rgb(161,255,161)">0.3702303</td>
      <td align="right" style="background-color: rgb(255,233,233)">-0.08892755</td>
      <td align="right" style="background-color: rgb(255,215,215)">-0.1598127</td>
      <td align="right" style="background-color: rgb(255,211,211)">-0.172454</td>
      <td align="right" style="background-color: rgb(255,226,226)">-0.1154492</td>
      <td align="right" style="background-color: rgb(255,228,228)">-0.109083</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2353861</td>
      <td align="right" style="background-color: rgb(255,244,244)">-0.04385902</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1223091</td>
      <td align="right" style="background-color: rgb(233,255,233)">0.08747504</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(255,227,227)">-0.1131149</td>
      <td align="right" style="background-color: rgb(255,213,213)">-0.1652464</td>
      <td align="right" style="background-color: rgb(255,213,213)">-0.1676933</td>
      <td align="right" style="background-color: rgb(255,250,250)">-0.02315599</td>
      <td align="right" style="background-color: rgb(251,255,251)">0.01641069</td>
      <td align="right" style="background-color: rgb(255,225,225)">-0.1193673</td>
      <td align="right" style="background-color: rgb(255,232,232)">-0.09364463</td>
      <td align="right" style="background-color: rgb(253,255,253)">0.008689379</td>
      <td align="right" style="background-color: rgb(255,212,212)">-0.1682108</td>
      <td align="right" style="background-color: rgb(255,226,226)">-0.1143665</td>
      <td align="right" style="background-color: rgb(255,247,247)">-0.03204645</td>
      <td align="right" style="background-color: rgb(255,212,212)">-0.1692707</td>
      <td align="right" style="background-color: rgb(255,241,241)">-0.05469794</td>
      <td align="right" style="background-color: rgb(255,239,239)">-0.06385817</td>
      <td align="right" style="background-color: rgb(255,255,255)">0.002133147</td>
      <td align="right" style="background-color: rgb(255,253,253)">-0.009516218</td>
      <td align="right" style="background-color: rgb(255,246,246)">-0.03548626</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_13_When buying a boat  I tend to buy the latest and greatest</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1225231</td>
      <td align="right" style="background-color: rgb(254,255,254)">0.006216449</td>
      <td align="right" style="background-color: rgb(131,255,131)">0.4845101</td>
      <td align="right" style="background-color: rgb(186,255,186)">0.2726845</td>
      <td align="right" style="background-color: rgb(140,255,140)">0.4503552</td>
      <td align="right" style="background-color: rgb(182,255,182)">0.2856959</td>
      <td align="right" style="background-color: rgb(166,255,166)">0.3489323</td>
      <td align="right" style="background-color: rgb(255,243,243)">-0.04788385</td>
      <td align="right" style="background-color: rgb(133,255,133)">0.4801163</td>
      <td align="right" style="background-color: rgb(214,255,214)">0.1614156</td>
      <td align="right" style="background-color: rgb(235,255,235)">0.07991006</td>
      <td align="right" style="background-color: rgb(255,227,227)">-0.1131149</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(92,255,92)">0.638152</td>
      <td align="right" style="background-color: rgb(138,255,138)">0.4576596</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4270921</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4258769</td>
      <td align="right" style="background-color: rgb(203,255,203)">0.2035355</td>
      <td align="right" style="background-color: rgb(227,255,227)">0.1110694</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.386806</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.1354077</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2301104</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.31869</td>
      <td align="right" style="background-color: rgb(205,255,205)">0.1963388</td>
      <td align="right" style="background-color: rgb(173,255,173)">0.3234327</td>
      <td align="right" style="background-color: rgb(132,255,132)">0.4809972</td>
      <td align="right" style="background-color: rgb(154,255,154)">0.3981403</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.4040972</td>
      <td align="right" style="background-color: rgb(207,255,207)">0.19034</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_14_When buying accessories for my boat  I tend to buy the latest and greatest</td>
      <td align="right" style="background-color: rgb(210,255,210)">0.1785</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.03047899</td>
      <td align="right" style="background-color: rgb(137,255,137)">0.4615334</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2941087</td>
      <td align="right" style="background-color: rgb(138,255,138)">0.4599086</td>
      <td align="right" style="background-color: rgb(175,255,175)">0.3137982</td>
      <td align="right" style="background-color: rgb(163,255,163)">0.3619325</td>
      <td align="right" style="background-color: rgb(255,250,250)">-0.02173115</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4267455</td>
      <td align="right" style="background-color: rgb(229,255,229)">0.1051007</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.1345263</td>
      <td align="right" style="background-color: rgb(255,213,213)">-0.1652464</td>
      <td align="right" style="background-color: rgb(92,255,92)">0.638152</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(128,255,128)">0.499926</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4272475</td>
      <td align="right" style="background-color: rgb(154,255,154)">0.3976384</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2493042</td>
      <td align="right" style="background-color: rgb(210,255,210)">0.1773178</td>
      <td align="right" style="background-color: rgb(151,255,151)">0.4065287</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2082177</td>
      <td align="right" style="background-color: rgb(183,255,183)">0.2851539</td>
      <td align="right" style="background-color: rgb(164,255,164)">0.3564865</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2089843</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3532649</td>
      <td align="right" style="background-color: rgb(136,255,136)">0.4649381</td>
      <td align="right" style="background-color: rgb(155,255,155)">0.3933706</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.4048601</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2109205</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_15_I am serious about the technology on my boat</td>
      <td align="right" style="background-color: rgb(189,255,189)">0.2610791</td>
      <td align="right" style="background-color: rgb(255,236,236)">-0.07768844</td>
      <td align="right" style="background-color: rgb(159,255,159)">0.3762223</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2961264</td>
      <td align="right" style="background-color: rgb(149,255,149)">0.4176032</td>
      <td align="right" style="background-color: rgb(175,255,175)">0.314295</td>
      <td align="right" style="background-color: rgb(167,255,167)">0.3448759</td>
      <td align="right" style="background-color: rgb(240,255,240)">0.06131853</td>
      <td align="right" style="background-color: rgb(170,255,170)">0.3327023</td>
      <td align="right" style="background-color: rgb(227,255,227)">0.1111225</td>
      <td align="right" style="background-color: rgb(203,255,203)">0.2049692</td>
      <td align="right" style="background-color: rgb(255,213,213)">-0.1676933</td>
      <td align="right" style="background-color: rgb(138,255,138)">0.4576596</td>
      <td align="right" style="background-color: rgb(128,255,128)">0.499926</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(150,255,150)">0.4117403</td>
      <td align="right" style="background-color: rgb(155,255,155)">0.3943083</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3164233</td>
      <td align="right" style="background-color: rgb(188,255,188)">0.2634045</td>
      <td align="right" style="background-color: rgb(151,255,151)">0.4069517</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2100431</td>
      <td align="right" style="background-color: rgb(172,255,172)">0.3263548</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3529761</td>
      <td align="right" style="background-color: rgb(188,255,188)">0.2655171</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4280453</td>
      <td align="right" style="background-color: rgb(160,255,160)">0.3732072</td>
      <td align="right" style="background-color: rgb(166,255,166)">0.3503511</td>
      <td align="right" style="background-color: rgb(159,255,159)">0.3783582</td>
      <td align="right" style="background-color: rgb(193,255,193)">0.2449105</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_16_People tend to come to me for advice about boating</td>
      <td align="right" style="background-color: rgb(215,255,215)">0.1571813</td>
      <td align="right" style="background-color: rgb(255,252,252)">-0.01528283</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.3871884</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1820797</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3552757</td>
      <td align="right" style="background-color: rgb(186,255,186)">0.2717595</td>
      <td align="right" style="background-color: rgb(176,255,176)">0.309052</td>
      <td align="right" style="background-color: rgb(250,255,250)">0.02284145</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.389195</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.03011578</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3192129</td>
      <td align="right" style="background-color: rgb(255,250,250)">-0.02315599</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4270921</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4272475</td>
      <td align="right" style="background-color: rgb(150,255,150)">0.4117403</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(94,255,94)">0.6314321</td>
      <td align="right" style="background-color: rgb(204,255,204)">0.202915</td>
      <td align="right" style="background-color: rgb(220,255,220)">0.1379903</td>
      <td align="right" style="background-color: rgb(122,255,122)">0.5215532</td>
      <td align="right" style="background-color: rgb(215,255,215)">0.1584056</td>
      <td align="right" style="background-color: rgb(179,255,179)">0.300045</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.3996333</td>
      <td align="right" style="background-color: rgb(206,255,206)">0.1941001</td>
      <td align="right" style="background-color: rgb(157,255,157)">0.3857702</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.4020004</td>
      <td align="right" style="background-color: rgb(134,255,134)">0.4758203</td>
      <td align="right" style="background-color: rgb(128,255,128)">0.4964176</td>
      <td align="right" style="background-color: rgb(204,255,204)">0.2019936</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_17_I consider myself more knowledgeable about boating than the rest of my boating peers</td>
      <td align="right" style="background-color: rgb(218,255,218)">0.1478382</td>
      <td align="right" style="background-color: rgb(246,255,246)">0.03891559</td>
      <td align="right" style="background-color: rgb(158,255,158)">0.3790491</td>
      <td align="right" style="background-color: rgb(211,255,211)">0.1748554</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3183953</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2361925</td>
      <td align="right" style="background-color: rgb(182,255,182)">0.2852205</td>
      <td align="right" style="background-color: rgb(243,255,243)">0.04813343</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3656044</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.02844251</td>
      <td align="right" style="background-color: rgb(177,255,177)">0.3079996</td>
      <td align="right" style="background-color: rgb(251,255,251)">0.01641069</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4258769</td>
      <td align="right" style="background-color: rgb(154,255,154)">0.3976384</td>
      <td align="right" style="background-color: rgb(155,255,155)">0.3943083</td>
      <td align="right" style="background-color: rgb(94,255,94)">0.6314321</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(212,255,212)">0.1709395</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1219496</td>
      <td align="right" style="background-color: rgb(141,255,141)">0.4455985</td>
      <td align="right" style="background-color: rgb(223,255,223)">0.1255432</td>
      <td align="right" style="background-color: rgb(189,255,189)">0.2584398</td>
      <td align="right" style="background-color: rgb(163,255,163)">0.3631356</td>
      <td align="right" style="background-color: rgb(217,255,217)">0.1485959</td>
      <td align="right" style="background-color: rgb(163,255,163)">0.3624441</td>
      <td align="right" style="background-color: rgb(154,255,154)">0.398115</td>
      <td align="right" style="background-color: rgb(143,255,143)">0.4378608</td>
      <td align="right" style="background-color: rgb(137,255,137)">0.4624776</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2094042</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_18_Boating gives me a feeling of adventure</td>
      <td align="right" style="background-color: rgb(191,255,191)">0.2532779</td>
      <td align="right" style="background-color: rgb(255,246,246)">-0.0377051</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2379419</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1845094</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2341611</td>
      <td align="right" style="background-color: rgb(143,255,143)">0.4375378</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.4009004</td>
      <td align="right" style="background-color: rgb(237,255,237)">0.07380629</td>
      <td align="right" style="background-color: rgb(200,255,200)">0.218012</td>
      <td align="right" style="background-color: rgb(220,255,220)">0.1406122</td>
      <td align="right" style="background-color: rgb(227,255,227)">0.1119335</td>
      <td align="right" style="background-color: rgb(255,225,225)">-0.1193673</td>
      <td align="right" style="background-color: rgb(203,255,203)">0.2035355</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2493042</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3164233</td>
      <td align="right" style="background-color: rgb(204,255,204)">0.202915</td>
      <td align="right" style="background-color: rgb(212,255,212)">0.1709395</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(131,255,131)">0.487302</td>
      <td align="right" style="background-color: rgb(184,255,184)">0.2810539</td>
      <td align="right" style="background-color: rgb(134,255,134)">0.4727972</td>
      <td align="right" style="background-color: rgb(144,255,144)">0.4370254</td>
      <td align="right" style="background-color: rgb(181,255,181)">0.2902856</td>
      <td align="right" style="background-color: rgb(147,255,147)">0.4227029</td>
      <td align="right" style="background-color: rgb(160,255,160)">0.3722258</td>
      <td align="right" style="background-color: rgb(194,255,194)">0.2385513</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2466674</td>
      <td align="right" style="background-color: rgb(175,255,175)">0.3127664</td>
      <td align="right" style="background-color: rgb(179,255,179)">0.2991944</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_19_Boating allows me to experience nature</td>
      <td align="right" style="background-color: rgb(185,255,185)">0.2739737</td>
      <td align="right" style="background-color: rgb(255,246,246)">-0.03631476</td>
      <td align="right" style="background-color: rgb(219,255,219)">0.1413975</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1854829</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1842438</td>
      <td align="right" style="background-color: rgb(164,255,164)">0.35552</td>
      <td align="right" style="background-color: rgb(183,255,183)">0.2815365</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09497647</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07439851</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09458814</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1233462</td>
      <td align="right" style="background-color: rgb(255,232,232)">-0.09364463</td>
      <td align="right" style="background-color: rgb(227,255,227)">0.1110694</td>
      <td align="right" style="background-color: rgb(210,255,210)">0.1773178</td>
      <td align="right" style="background-color: rgb(188,255,188)">0.2634045</td>
      <td align="right" style="background-color: rgb(220,255,220)">0.1379903</td>
      <td align="right" style="background-color: rgb(224,255,224)">0.1219496</td>
      <td align="right" style="background-color: rgb(131,255,131)">0.487302</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(201,255,201)">0.2130091</td>
      <td align="right" style="background-color: rgb(143,255,143)">0.4400385</td>
      <td align="right" style="background-color: rgb(158,255,158)">0.3800002</td>
      <td align="right" style="background-color: rgb(193,255,193)">0.2436489</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3658044</td>
      <td align="right" style="background-color: rgb(173,255,173)">0.3238644</td>
      <td align="right" style="background-color: rgb(220,255,220)">0.1393575</td>
      <td align="right" style="background-color: rgb(211,255,211)">0.1756306</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2319771</td>
      <td align="right" style="background-color: rgb(184,255,184)">0.2788318</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_20_When not on my boat  I often find myself doing boating related activities</td>
      <td align="right" style="background-color: rgb(206,255,206)">0.1941126</td>
      <td align="right" style="background-color: rgb(242,255,242)">0.05335306</td>
      <td align="right" style="background-color: rgb(157,255,157)">0.3855504</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1832706</td>
      <td align="right" style="background-color: rgb(173,255,173)">0.322899</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3540081</td>
      <td align="right" style="background-color: rgb(163,255,163)">0.363264</td>
      <td align="right" style="background-color: rgb(244,255,244)">0.04331111</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3659377</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09627565</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2499986</td>
      <td align="right" style="background-color: rgb(253,255,253)">0.008689379</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.386806</td>
      <td align="right" style="background-color: rgb(151,255,151)">0.4065287</td>
      <td align="right" style="background-color: rgb(151,255,151)">0.4069517</td>
      <td align="right" style="background-color: rgb(122,255,122)">0.5215532</td>
      <td align="right" style="background-color: rgb(141,255,141)">0.4455985</td>
      <td align="right" style="background-color: rgb(184,255,184)">0.2810539</td>
      <td align="right" style="background-color: rgb(201,255,201)">0.2130091</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(198,255,198)">0.2257927</td>
      <td align="right" style="background-color: rgb(170,255,170)">0.3346061</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.4045244</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2375164</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.4056079</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.403381</td>
      <td align="right" style="background-color: rgb(127,255,127)">0.5032943</td>
      <td align="right" style="background-color: rgb(122,255,122)">0.5202893</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2472896</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_21_Boating helps me escape from everyday life and relax</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2352835</td>
      <td align="right" style="background-color: rgb(255,230,230)">-0.09945353</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1819674</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1830434</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1872704</td>
      <td align="right" style="background-color: rgb(147,255,147)">0.4242353</td>
      <td align="right" style="background-color: rgb(172,255,172)">0.3273714</td>
      <td align="right" style="background-color: rgb(239,255,239)">0.06314187</td>
      <td align="right" style="background-color: rgb(219,255,219)">0.1435208</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07687198</td>
      <td align="right" style="background-color: rgb(222,255,222)">0.1291384</td>
      <td align="right" style="background-color: rgb(255,212,212)">-0.1682108</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.1354077</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2082177</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2100431</td>
      <td align="right" style="background-color: rgb(215,255,215)">0.1584056</td>
      <td align="right" style="background-color: rgb(223,255,223)">0.1255432</td>
      <td align="right" style="background-color: rgb(134,255,134)">0.4727972</td>
      <td align="right" style="background-color: rgb(143,255,143)">0.4400385</td>
      <td align="right" style="background-color: rgb(198,255,198)">0.2257927</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(148,255,148)">0.4212274</td>
      <td align="right" style="background-color: rgb(194,255,194)">0.2391254</td>
      <td align="right" style="background-color: rgb(147,255,147)">0.4241711</td>
      <td align="right" style="background-color: rgb(178,255,178)">0.3021626</td>
      <td align="right" style="background-color: rgb(218,255,218)">0.1478099</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2356413</td>
      <td align="right" style="background-color: rgb(189,255,189)">0.2603983</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2942509</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_22_Boating helps me stay active</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2314947</td>
      <td align="right" style="background-color: rgb(255,236,236)">-0.07644686</td>
      <td align="right" style="background-color: rgb(183,255,183)">0.281364</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2335025</td>
      <td align="right" style="background-color: rgb(185,255,185)">0.2737216</td>
      <td align="right" style="background-color: rgb(151,255,151)">0.4088023</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.3901573</td>
      <td align="right" style="background-color: rgb(242,255,242)">0.05411788</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.232465</td>
      <td align="right" style="background-color: rgb(232,255,232)">0.09113168</td>
      <td align="right" style="background-color: rgb(212,255,212)">0.1700732</td>
      <td align="right" style="background-color: rgb(255,226,226)">-0.1143665</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2301104</td>
      <td align="right" style="background-color: rgb(183,255,183)">0.2851539</td>
      <td align="right" style="background-color: rgb(172,255,172)">0.3263548</td>
      <td align="right" style="background-color: rgb(179,255,179)">0.300045</td>
      <td align="right" style="background-color: rgb(189,255,189)">0.2584398</td>
      <td align="right" style="background-color: rgb(144,255,144)">0.4370254</td>
      <td align="right" style="background-color: rgb(158,255,158)">0.3800002</td>
      <td align="right" style="background-color: rgb(170,255,170)">0.3346061</td>
      <td align="right" style="background-color: rgb(148,255,148)">0.4212274</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(169,255,169)">0.3367852</td>
      <td align="right" style="background-color: rgb(158,255,158)">0.382792</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3662357</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2320061</td>
      <td align="right" style="background-color: rgb(167,255,167)">0.3458454</td>
      <td align="right" style="background-color: rgb(159,255,159)">0.3756358</td>
      <td align="right" style="background-color: rgb(168,255,168)">0.341154</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_23_Boating allows me to excel in the sports that I am passionate about   e g  fishing  racing  water sports </td>
      <td align="right" style="background-color: rgb(207,255,207)">0.1875854</td>
      <td align="right" style="background-color: rgb(255,255,255)">0.002846742</td>
      <td align="right" style="background-color: rgb(169,255,169)">0.3395666</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1642283</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2934292</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3179028</td>
      <td align="right" style="background-color: rgb(178,255,178)">0.3044174</td>
      <td align="right" style="background-color: rgb(230,255,230)">0.09931021</td>
      <td align="right" style="background-color: rgb(182,255,182)">0.2886866</td>
      <td align="right" style="background-color: rgb(238,255,238)">0.06954759</td>
      <td align="right" style="background-color: rgb(206,255,206)">0.1920789</td>
      <td align="right" style="background-color: rgb(255,247,247)">-0.03204645</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.31869</td>
      <td align="right" style="background-color: rgb(164,255,164)">0.3564865</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3529761</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.3996333</td>
      <td align="right" style="background-color: rgb(163,255,163)">0.3631356</td>
      <td align="right" style="background-color: rgb(181,255,181)">0.2902856</td>
      <td align="right" style="background-color: rgb(193,255,193)">0.2436489</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.4045244</td>
      <td align="right" style="background-color: rgb(194,255,194)">0.2391254</td>
      <td align="right" style="background-color: rgb(169,255,169)">0.3367852</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2302928</td>
      <td align="right" style="background-color: rgb(173,255,173)">0.3237862</td>
      <td align="right" style="background-color: rgb(171,255,171)">0.3309736</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.3903706</td>
      <td align="right" style="background-color: rgb(143,255,143)">0.438619</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2343864</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_24_Boating gives me an outlet to socialize with family and or friends</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2091071</td>
      <td align="right" style="background-color: rgb(255,236,236)">-0.07550207</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2276743</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2291016</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.249245</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.366991</td>
      <td align="right" style="background-color: rgb(170,255,170)">0.3327883</td>
      <td align="right" style="background-color: rgb(251,255,251)">0.01860354</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2304275</td>
      <td align="right" style="background-color: rgb(222,255,222)">0.131241</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07730115</td>
      <td align="right" style="background-color: rgb(255,212,212)">-0.1692707</td>
      <td align="right" style="background-color: rgb(205,255,205)">0.1963388</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2089843</td>
      <td align="right" style="background-color: rgb(188,255,188)">0.2655171</td>
      <td align="right" style="background-color: rgb(206,255,206)">0.1941001</td>
      <td align="right" style="background-color: rgb(217,255,217)">0.1485959</td>
      <td align="right" style="background-color: rgb(147,255,147)">0.4227029</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3658044</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2375164</td>
      <td align="right" style="background-color: rgb(147,255,147)">0.4241711</td>
      <td align="right" style="background-color: rgb(158,255,158)">0.382792</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2302928</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(177,255,177)">0.3058189</td>
      <td align="right" style="background-color: rgb(203,255,203)">0.2051045</td>
      <td align="right" style="background-color: rgb(193,255,193)">0.2442175</td>
      <td align="right" style="background-color: rgb(190,255,190)">0.2546505</td>
      <td align="right" style="background-color: rgb(186,255,186)">0.2712524</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_25_Being in charge of my boat is very important to me</td>
      <td align="right" style="background-color: rgb(197,255,197)">0.2270835</td>
      <td align="right" style="background-color: rgb(253,255,253)">0.008885516</td>
      <td align="right" style="background-color: rgb(164,255,164)">0.3580322</td>
      <td align="right" style="background-color: rgb(200,255,200)">0.2180119</td>
      <td align="right" style="background-color: rgb(181,255,181)">0.2902679</td>
      <td align="right" style="background-color: rgb(148,255,148)">0.4200361</td>
      <td align="right" style="background-color: rgb(148,255,148)">0.4194157</td>
      <td align="right" style="background-color: rgb(230,255,230)">0.09905621</td>
      <td align="right" style="background-color: rgb(174,255,174)">0.3190602</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07601007</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2488671</td>
      <td align="right" style="background-color: rgb(255,241,241)">-0.05469794</td>
      <td align="right" style="background-color: rgb(173,255,173)">0.3234327</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3532649</td>
      <td align="right" style="background-color: rgb(146,255,146)">0.4280453</td>
      <td align="right" style="background-color: rgb(157,255,157)">0.3857702</td>
      <td align="right" style="background-color: rgb(163,255,163)">0.3624441</td>
      <td align="right" style="background-color: rgb(160,255,160)">0.3722258</td>
      <td align="right" style="background-color: rgb(173,255,173)">0.3238644</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.4056079</td>
      <td align="right" style="background-color: rgb(178,255,178)">0.3021626</td>
      <td align="right" style="background-color: rgb(162,255,162)">0.3662357</td>
      <td align="right" style="background-color: rgb(173,255,173)">0.3237862</td>
      <td align="right" style="background-color: rgb(177,255,177)">0.3058189</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(169,255,169)">0.3364399</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3532394</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.4013018</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2334195</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_26_Having a powerful boat is what is most important to me</td>
      <td align="right" style="background-color: rgb(229,255,229)">0.1037838</td>
      <td align="right" style="background-color: rgb(237,255,237)">0.0737951</td>
      <td align="right" style="background-color: rgb(135,255,135)">0.4710066</td>
      <td align="right" style="background-color: rgb(206,255,206)">0.1922681</td>
      <td align="right" style="background-color: rgb(169,255,169)">0.3372278</td>
      <td align="right" style="background-color: rgb(177,255,177)">0.3073585</td>
      <td align="right" style="background-color: rgb(157,255,157)">0.3864856</td>
      <td align="right" style="background-color: rgb(255,244,244)">-0.04453738</td>
      <td align="right" style="background-color: rgb(127,255,127)">0.5026779</td>
      <td align="right" style="background-color: rgb(221,255,221)">0.1348247</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09385587</td>
      <td align="right" style="background-color: rgb(255,239,239)">-0.06385817</td>
      <td align="right" style="background-color: rgb(132,255,132)">0.4809972</td>
      <td align="right" style="background-color: rgb(136,255,136)">0.4649381</td>
      <td align="right" style="background-color: rgb(160,255,160)">0.3732072</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.4020004</td>
      <td align="right" style="background-color: rgb(154,255,154)">0.398115</td>
      <td align="right" style="background-color: rgb(194,255,194)">0.2385513</td>
      <td align="right" style="background-color: rgb(220,255,220)">0.1393575</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.403381</td>
      <td align="right" style="background-color: rgb(218,255,218)">0.1478099</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2320061</td>
      <td align="right" style="background-color: rgb(171,255,171)">0.3309736</td>
      <td align="right" style="background-color: rgb(203,255,203)">0.2051045</td>
      <td align="right" style="background-color: rgb(169,255,169)">0.3364399</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(140,255,140)">0.4503873</td>
      <td align="right" style="background-color: rgb(134,255,134)">0.4729243</td>
      <td align="right" style="background-color: rgb(217,255,217)">0.1498648</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_27_Boating is the number one thing I do with my spare time</td>
      <td align="right" style="background-color: rgb(223,255,223)">0.1268492</td>
      <td align="right" style="background-color: rgb(244,255,244)">0.04546034</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.4008411</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1650017</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2940066</td>
      <td align="right" style="background-color: rgb(167,255,167)">0.3446675</td>
      <td align="right" style="background-color: rgb(161,255,161)">0.370631</td>
      <td align="right" style="background-color: rgb(248,255,248)">0.02919826</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.3996665</td>
      <td align="right" style="background-color: rgb(236,255,236)">0.07710982</td>
      <td align="right" style="background-color: rgb(215,255,215)">0.1570309</td>
      <td align="right" style="background-color: rgb(255,255,255)">0.002133147</td>
      <td align="right" style="background-color: rgb(154,255,154)">0.3981403</td>
      <td align="right" style="background-color: rgb(155,255,155)">0.3933706</td>
      <td align="right" style="background-color: rgb(166,255,166)">0.3503511</td>
      <td align="right" style="background-color: rgb(134,255,134)">0.4758203</td>
      <td align="right" style="background-color: rgb(143,255,143)">0.4378608</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2466674</td>
      <td align="right" style="background-color: rgb(211,255,211)">0.1756306</td>
      <td align="right" style="background-color: rgb(127,255,127)">0.5032943</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2356413</td>
      <td align="right" style="background-color: rgb(167,255,167)">0.3458454</td>
      <td align="right" style="background-color: rgb(156,255,156)">0.3903706</td>
      <td align="right" style="background-color: rgb(193,255,193)">0.2442175</td>
      <td align="right" style="background-color: rgb(165,255,165)">0.3532394</td>
      <td align="right" style="background-color: rgb(140,255,140)">0.4503873</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(98,255,98)">0.6153207</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2336201</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_28_Boating is my true passion in life</td>
      <td align="right" style="background-color: rgb(210,255,210)">0.1760324</td>
      <td align="right" style="background-color: rgb(251,255,251)">0.01601573</td>
      <td align="right" style="background-color: rgb(147,255,147)">0.4252522</td>
      <td align="right" style="background-color: rgb(201,255,201)">0.2124064</td>
      <td align="right" style="background-color: rgb(172,255,172)">0.3250107</td>
      <td align="right" style="background-color: rgb(155,255,155)">0.3924007</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.3993589</td>
      <td align="right" style="background-color: rgb(244,255,244)">0.04578701</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.40248</td>
      <td align="right" style="background-color: rgb(238,255,238)">0.06921813</td>
      <td align="right" style="background-color: rgb(209,255,209)">0.1829313</td>
      <td align="right" style="background-color: rgb(255,253,253)">-0.009516218</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.4040972</td>
      <td align="right" style="background-color: rgb(152,255,152)">0.4048601</td>
      <td align="right" style="background-color: rgb(159,255,159)">0.3783582</td>
      <td align="right" style="background-color: rgb(128,255,128)">0.4964176</td>
      <td align="right" style="background-color: rgb(137,255,137)">0.4624776</td>
      <td align="right" style="background-color: rgb(175,255,175)">0.3127664</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2319771</td>
      <td align="right" style="background-color: rgb(122,255,122)">0.5202893</td>
      <td align="right" style="background-color: rgb(189,255,189)">0.2603983</td>
      <td align="right" style="background-color: rgb(159,255,159)">0.3756358</td>
      <td align="right" style="background-color: rgb(143,255,143)">0.438619</td>
      <td align="right" style="background-color: rgb(190,255,190)">0.2546505</td>
      <td align="right" style="background-color: rgb(153,255,153)">0.4013018</td>
      <td align="right" style="background-color: rgb(134,255,134)">0.4729243</td>
      <td align="right" style="background-color: rgb(98,255,98)">0.6153207</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
      <td align="right" style="background-color: rgb(189,255,189)">0.2608264</td>
    </tr>
    <tr>
      <td align="center" style="font-size:10px;">Q1_29_Boating is one of many things I do in my spare time</td>
      <td align="right" style="background-color: rgb(204,255,204)">0.2016025</td>
      <td align="right" style="background-color: rgb(255,248,248)">-0.02895487</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1659069</td>
      <td align="right" style="background-color: rgb(208,255,208)">0.1865064</td>
      <td align="right" style="background-color: rgb(210,255,210)">0.1778252</td>
      <td align="right" style="background-color: rgb(186,255,186)">0.2714557</td>
      <td align="right" style="background-color: rgb(194,255,194)">0.2405801</td>
      <td align="right" style="background-color: rgb(231,255,231)">0.09731618</td>
      <td align="right" style="background-color: rgb(226,255,226)">0.1146627</td>
      <td align="right" style="background-color: rgb(242,255,242)">0.05107339</td>
      <td align="right" style="background-color: rgb(213,255,213)">0.1659397</td>
      <td align="right" style="background-color: rgb(255,246,246)">-0.03548626</td>
      <td align="right" style="background-color: rgb(207,255,207)">0.19034</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2109205</td>
      <td align="right" style="background-color: rgb(193,255,193)">0.2449105</td>
      <td align="right" style="background-color: rgb(204,255,204)">0.2019936</td>
      <td align="right" style="background-color: rgb(202,255,202)">0.2094042</td>
      <td align="right" style="background-color: rgb(179,255,179)">0.2991944</td>
      <td align="right" style="background-color: rgb(184,255,184)">0.2788318</td>
      <td align="right" style="background-color: rgb(192,255,192)">0.2472896</td>
      <td align="right" style="background-color: rgb(180,255,180)">0.2942509</td>
      <td align="right" style="background-color: rgb(168,255,168)">0.341154</td>
      <td align="right" style="background-color: rgb(195,255,195)">0.2343864</td>
      <td align="right" style="background-color: rgb(186,255,186)">0.2712524</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2334195</td>
      <td align="right" style="background-color: rgb(217,255,217)">0.1498648</td>
      <td align="right" style="background-color: rgb(196,255,196)">0.2336201</td>
      <td align="right" style="background-color: rgb(189,255,189)">0.2608264</td>
      <td align="right" style="background-color: rgb(0,255,0)">1.00</td>
    </tr>
  </tbody>
</table>

</div>
</div>
### Number of Factors

There are three common ways to select the optimal number of factors from a statistical perspective:

1. All factors with eigenvalue larger than 1

2. Based on the cumulative variance we would like to explain (e.g. at least 50% for example)

3. Pick the number of factors corresponding to the "elbow" of the scree plot

The first two approaches to select the number of factors/derived variables can be seen in the following table: 


<!-- Table generated in R 4.2.3 by googleVis 0.7.3 package -->
<!-- Fri Jul 26 22:06:29 2024 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataTableID56c62beeec58 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
"Component No:1",
"8.43258755631198",
"29.0778881252138",
"29.0778881252138"
],
[
"Component No:2",
"2.33361053973262",
"8.04693289562975",
"37.1248210208435"
],
[
"Component No:3",
"1.86276159622213",
"6.42331584904184",
"43.5481368698854"
],
[
"Component No:4",
"1.45760376008889",
"5.02621986237549",
"48.5743567322609"
],
[
"Component No:5",
"1.2073695374066",
"4.16334323243657",
"52.7376999646974"
],
[
"Component No:6",
"0.898314004439866",
"3.09763449806851",
"55.8353344627659"
],
[
"Component No:7",
"0.816772272062009",
"2.81645611055866",
"58.6517905733246"
],
[
"Component No:8",
"0.786338039233822",
"2.71151048011663",
"61.3633010534412"
],
[
"Component No:9",
"0.780445603335745",
"2.69119173564051",
"64.0544927890817"
],
[
"Component No:10",
"0.741323089951169",
"2.556286517073",
"66.6107793061547"
],
[
"Component No:11",
"0.68663248264883",
"2.36769821603045",
"68.9784775221852"
],
[
"Component No:12",
"0.653629766951428",
"2.25389574810838",
"71.2323732702936"
],
[
"Component No:13",
"0.647940387417508",
"2.23427719799141",
"73.466650468285"
],
[
"Component No:14",
"0.617977318288445",
"2.13095626996016",
"75.5976067382451"
],
[
"Component No:15",
"0.609075263240892",
"2.10025952841687",
"77.697866266662"
],
[
"Component No:16",
"0.576480197091234",
"1.98786274859047",
"79.6857290152524"
],
[
"Component No:17",
"0.561694660361798",
"1.93687813917862",
"81.6226071544311"
],
[
"Component No:18",
"0.536510145417632",
"1.85003498419873",
"83.4726421386298"
],
[
"Component No:19",
"0.524119414334147",
"1.80730832529017",
"85.27995046392"
],
[
"Component No:20",
"0.511210019792466",
"1.76279317169816",
"87.0427436356181"
],
[
"Component No:21",
"0.499501041469187",
"1.72241738437651",
"88.7651610199946"
],
[
"Component No:22",
"0.489037857044931",
"1.68633743808597",
"90.4514984580806"
],
[
"Component No:23",
"0.460670106390301",
"1.58851760824242",
"92.040016066323"
],
[
"Component No:24",
"0.455964735262793",
"1.57229219056136",
"93.6123082568844"
],
[
"Component No:25",
"0.411890964303778",
"1.42031367001303",
"95.0326219268974"
],
[
"Component No:26",
"0.383613638068462",
"1.32280564851194",
"96.3554275754094"
],
[
"Component No:27",
"0.369997341276257",
"1.27585290095261",
"97.631280476362"
],
[
"Component No:28",
"0.352424285652573",
"1.21525615742267",
"98.8465366337847"
],
[
"Component No:29",
"0.334504376202451",
"1.15346336621535",
"100"
] 
];
data.addColumn('string','Components');
data.addColumn('string','Eigenvalue');
data.addColumn('string','Percentage_of_explained_variance');
data.addColumn('string','Cumulative_percentage_of_explained_variance');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartTableID56c62beeec58() {
var data = gvisDataTableID56c62beeec58();
var options = {};
options["allowHtml"] = true;
options["width"] = 1200;
options["height"] = 400;
options["allowHTML"] = true;
options["page"] = "disable";

  var dataFormat1 = new google.visualization.NumberFormat({pattern:"#.##"});
  dataFormat1.format(data, 1);
  var dataFormat2 = new google.visualization.NumberFormat({pattern:"#.##"});
  dataFormat2.format(data, 2);
  var dataFormat3 = new google.visualization.NumberFormat({pattern:"#.##"});
  dataFormat3.format(data, 3);

    var chart = new google.visualization.Table(
    document.getElementById('TableID56c62beeec58')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "table";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartTableID56c62beeec58);
})();
function displayChartTableID56c62beeec58() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartTableID56c62beeec58"></script>
 
<!-- divChart -->
  
<div id="TableID56c62beeec58" 
  style="width: 1200; height: 400;">
</div>






























