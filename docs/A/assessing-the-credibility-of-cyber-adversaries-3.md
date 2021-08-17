---
layout: default
title: Proposed Model for Online Adversary Credibility Assessment
parent: § Assessing the Credibility of Cyber Adversaries   
grand_parent: A 
nav_order: 30
---
<style>
.dont-break-out {
  /* These are technically the same, but use both */
  overflow-wrap: break-word;
  word-wrap: break-word;

     -ms-word-break: break-all;
  /* This is the dangerous one in WebKit, as it breaks things wherever */
  word-break: break-all;
  /* Instead use this non-standard one: */
  word-break: break-word;
}

.youtube-container {
    position: relative;
    width: 100%;
    height: 0;
    padding-bottom: 56.25%;
}
.youtube-video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
}

</style>

<div class="dont-break-out" markdown="1">
1. TOC
{:toc}

## Proposed Model for Online Adversary Credibility Assessment
There is no existing model defining online adversary credibility assessment. However, there are common themes and useful constructs in the previously discussed models that can assist us in looking at adversary credibility. This proposed model provides an exploratory method for assessing credibility of cyber actors who have deceptive or malicious intent, which fills a current gap in the literature. Across the models, we have identified three main characteristics - information, user, and interaction characteristics - as shown in Figure 2.

Assessing the Credibility of Cyber Adversaries

*Figure 2.* Proposed Model of Online Adversary Credibility Assessment

This paper has explored the scientific evidence for the validity of aspects of credibility and trust models, in order to develop a contemporary, plausible model of assessing adversary credibility. Existing theories of online credibility provide empirical evidence in support of the proposed model, the Online Adversary Credibility Assessment model, as shown in Table 3.

*Table 3.* Proposed domains of online credibility
![Proposed domains of online credibility](https://statics.bsafes.com/images/papers/assessing-the-credibility-of-cyber-adversaries-table-3.png)

### *Information Characteristics*
This model proposes that the first area for credibility assessment for potential adversaries should be in the characteristics of the information being presented. The majority of research and models have identified that information features are important for both System 1 and System 2 processing of credibility information. In this model, we have separated information characteristics into content features (i.e. the actual message), presentation features (i.e. the way the message is presented), technical features (i.e. the technical aspects of the content), and narrative consistency (i.e. how consistent the online information is over time).

Based on a large sample size, Fogg proposed that the source, message, and design are all important in credibility assessment (Fogg, 2003). Overall, they identified that content (e.g., accuracy, comprehensiveness, currency, reliability, and validity) and presentation features (e.g., the structure of the information/ website, technical functionality, aesthetic feel, and interaction design in terms of stability, consistency, and easiness) are fundamental aspects for credibility assessment.

Other information characteristics identified in the literature as demonstrating credibility include the expression of emotion, citing of external sources, strong design features, interactive elements, and level of certainty (Castillo, Mendoza, & Poblete, 2011; Sundar, 2008). Research has also used algorithms to identify credibility features, which include content-based features (e.g., high numbers of unique characters, swear words, pronouns, emojis) and user-based features (e.g., number of followers, length of username) (Alrubaian et al., 2019; Gupta & Kumaraguru, 2012; Karvonen, 2000). In recent work, the authors identified a number of source and message cues based on a review of empirical studies, outlined in Table 4 (Metzger & Flanagin, 2015).

*Table 4.* Metzger & Flanagin’s (2015) credibility features
![Metzger & Flanagin’s (2015) credibility features](https://statics.bsafes.com/images/papers/assessing-the-credibility-of-cyber-adversaries-table-4.png)

Technical features can also inform credibility assessment, particularly in the fraud detection literature. Network connectivity refers to attributes that reveal how a profile has connected to the internet and/or uses online platforms. Use of anonymization services (e.g., The Onion Router, proxies, Virtual Private Networks) is sometimes an indicator of suspicious behaviour and may cause additional scrutiny over an account. The Internet Protocol (IP) address associated with an account is also a key network connectivity feature. An account may be considered fraudulent or suspicious if the IP address associated with it was registered using the same registrar typically used by malicious actors or is in the same IP space as known malicious actors (Fukushima, Hori, & Sakurai, 2011; Moura, Sadre, & Pras, 2014). Geographic features paired with an IP also provide clues (e.g., the location of the IP does not match the stated geographic location of the user, the user registers and logs into the service from different IP address locations) (Robert, 2016). Accounts that claim to represent unique individuals but make use of data centre IP space instead of residential IP space are also worthy of additional scrutiny.

Device profile captures attributes associated with the device(s) used to register or access a specific platform; it is analogous to the aggregated trustworthiness model’s user profile concept (Jessen & Jørgensen, 2012). Browser fingerprinting is used to extract device profile features (e.g., user agent strings, language packages, screen resolution) from a user’s web browser.

Social graph refers to the account’s connectivity to other accounts and the evolution of this connectivity over time. Many social graph-based fraud detection approaches rely on the fact that fake accounts generally have fewer connections to real accounts and that fake accounts tend to cluster together. Related to this, it is also often assumed that accounts within a social network tend to be similar, so an account that deviates in appearance from other accounts in a social network it is linked to may be fraudulent (Mislove, Viswanath, Gummadi, & Druschel, 2010).

Observing how a social network forms over time speaks volumes about the authenticity of an account. For example, Facebook considers excessive friend requests suspicious (Robert, 2016). Research also suggests fake accounts (and in particular, automated accounts e.g., “bots”) spend their time much differently than authentic accounts; for example, fake accounts spend more time building new connections than interacting with existing connections (Wang, Konolige, Wilson, Wang, Zheng, & Zhao, 2013; Yang, Wilson, Wang, Gao, Zhao, & Dai, 2011).

Activity-based indicators include attributes related to the nature and frequency of activity on a single account or coordinated activities across multiple accounts. This includes temporal patterns; times of day an account is active, the frequency with which an account engages with content or other accounts on a platform, and the frequency with which an account creates/shares/ posts content. One study, using the Chinese social network Renren, found the number of sessions per user, number of sessions through the day, average session length per user, average number of clicks per user, and average time interval between clicks per session per user were all indicators of fake accounts (Yang et al., 2011).

Click analysis, typing speeds, and mouse movements are activity-based fraud indicators known as ‘behavioral biometrics’, such as Google’s ‘invisible’ CAPTCHA (Awad, 2017; Bo, Zhang, Li, Huang, & Wang, 2013). In one study, multiple accounts/identities managed by the same person were identified using features such as site familiarity and time taken to make posts (Tsikerdekis & Zeadally, 2014).

Campaigns of suspicious or manipulative activity can be detected by looking for coordinated activity or similar behavior across multiple accounts. For example, in one study authors uncovered over two million malicious accounts and 1,156 campaigns on Facebook and Instagram by identifying accounts that acted similarly at similar times in a sustained window of time (Cao, Yang, Yu, & Palow, 2014). As another example, researchers looking for coordinated patterns of activity on Twitter and various other platforms have identified many Russian-sponsored troll accounts (Jamieson, 2018).

A growing area of research in the fraud detection space related to user profiles is fake image detection. Companies such as Facebook and Airbnb have already employed various fake image detection techniques such as image hashing to detect the re-use of existing images. However, the rise of convincing “deep fake” image technology has prompted increased interest in developing statistical techniques to detect fake images used in online profiles (Menotti et al., 2015).

Narrative consistency is particularly important in adversary credibility assessment. In the proposed model, this is defined as the consistency of an online persona and online information over time. It includes both story consistency and personality presentation. Unfortunately, in more general models of online information credibility, narrative consistency has been neglected as a topic of research. The importance of narrative consistency, particularly in examining individual online accounts, is particularly relevant for heuristic processing. Research has shown that people expect consistency in presentations, and consistent presentations have greater influence over others than online presentations that are inconsistent (Isbister & Nass, 2000). When online contacts behave in an expected and consistent way, we are much less likely to apply System 2 thinking in a credibility assessment. In this model, we propose that examinations of narrative consistency in online information and profiles are essential in adversary credibility assessment.

The importance of content, technical features, and presentation are evidenced in the majority of the models discussed, such as modality in the MAIN model, source and surface characteristics in the dual processing models and information characteristics in the 3-S model. The growing fraud detection literature can help us identify additional technical indicators to support credibility assessment. Further examination of the validity of narrative consistency as a tool for detecting fake or adversary online personas is warranted.

### *User Characteristics*

Trustworthiness, expertise, dynamism, and attractiveness of the communicator are all relevant to judge overall credibility of the message (Fogg, 2003). In one study, researchers explored what characteristics shaped people’s perception of credibility on Twitter. The user’s influence, reputation, and topical expertise (judged from the user’s biography) resulted in enhanced perceived credibility (Morris, Counts, Roseway, Hoff, & Schwarz, 2012). In this proposed model of online adversary credibility, user characteristics are described as aspects of the online user (e.g., a potential adversary) that can indicate credibility concerns. This includes deception indicators and technical ability. Much of the previous discussion of fraud detection literature is pertinent here, but also the consistency of the technical ability with stated skills, backstory, and account settings are important to consider.

Deception indicators suggest intentional and misleading efforts to create a false belief in another. While such indicators are not specifically identified in the theoretical literature, trustworthiness and credibility are reliant on an honest or reliable relationship. Indicators of deception are contra-indicative to credibility. Digital deception requires manipulation enacted through a technologically enabled message (Donath, 1999; Hancock, 2012). However, deception detection is notoriously difficult and, on average, leads to an accuracy rate of not much greater than chance of around 55% (Vrij, 2000). This is because there are no obvious clues to deceit and the differences between liars and truth tellers are subtle.

Deception can be detected using both verbal and nonverbal cues. The empirically supported cognitive assessment approach to detecting deception uses cognitive techniques to elicit and enhance potential differences between truth tellers and liars. In a meta-analysis, this approach had accuracy rates of 71% versus 56% in a standard approach (Vrij, Fisher, & Blank, 2017). Through the cognitive assessment approach, research has identified a number of potential verbal cues including evidence of cognitive load, leakage, evidence of poor coping, inconsistent behavior, an absence of verifiable details, and lack of detail (Jupe, Leal, Vrij, & Nahari, 2017; Nahari, Vrij, & Fisher, 2012; Vrij et al., 2017). Nonverbal cues identified in the literature to differentiate between truth tellers and liars are related to methods such as working memory, attention, arousal, motivation, and self-presentation (Arciuli, Mallard, & Villar, 2010).

A language behavior approach assumes that a liar’s language reflects their emotions and cognitions (Toma & Hancock, 2010). Research on automated textual analysis suggests that there are detectable differences in linguistic patterns in communication that is true versus deceptive (Zhou & Zhang, 2008). In fact, some studies have shown that linguistic cues in deception can increase the ability to detect deception to 67% (Newman, Pennebaker, Berry, & Richards, 2003). Potential linguistic indicators of deception include a lack of rich details, reduced self-reference (e.g., ‘I’ statements), increased use of negations (e.g., ‘no’, ‘not’, ‘never’), being overly specific, having a lower number of named entities, and using fewer evaluations and judgments (Hauch, Blandón-Gitlin, Masip, & Sporer, 2015; Kleinberg, van der Toolen, Vrij, Arntz, & Verschuere, 2018; Masip, Sporer, Garrido & Herrero, 2005; Toma & Hancock, 2010).

Credibility may also be assessed by whether or not the stated technical expertise is commensurate with the back story and demonstrated technical ability. Following the construct of narrative consistency, this technical consistency is the demonstration that the online persona is as technically savvy as he or she proports. Claims of expertise in coding acumen, debugging techniques, or other technical skills can be compared to the cyber security practices they maintain as well as examples of their technical writing or any technical processes or procedures they discuss, publish, opine on, or demonstrate. The assessment of technical narrative characteristics naturally engages System 2 thinking, which is essential in determining credibility of potential adversaries or misleading personas. Thus deception indicators and inconsistencies in claims of technical expertise as compared to their lack of demonstrated technical expertise can highlight credibility concerns.

### *Interaction Characteristics*
Trust plays an important role in determining credibility within relationships. Credibility is intertwined with the concept of trust and is an inherent characteristic of meaningful and valuable social interaction (Cugelman, Thelwall, & Dawes, 2008; du Plessis, Angelopulo, & du Plessis, 2006; Fogg & Tseng, 1999). McKnight and Chervany created an interdisciplinary model of trust, which proposes that the many definitions of trust fall into different conceptual types: behaviors, beliefs, attitudes, and dispositions (McKnight & Chervany, 2000). They identified 16 trust-related characteristics, which were distilled to five conceptual categories of characteristics: benevolence, competence, predictability, integrity, and other (openness, carefulness, attractiveness, and shared understanding).

The aggregated trustworthiness model recognises how online credibility is influenced by social processes, such as followers and likes. The notion of social proofing is not new in influence psychology. Social validation is a similar concept – the more people that acknowledge information, the more likely it is to be perceived as credible (Cialdini, 2009; Metzger & Flanagin, 2015). Research has focussed on social online processes that influence credibility assessment. While traditionally authority figures provided opinion to influence credibility, experiential credibility means that people can now provide credible information on the basis of experience rather than authority (Pure et al., 2012). For example, customer reviews have been found to be stronger indicators of trustworthiness than store reputation (Utz, Kerkhof, & Van Den Bos, 2012). Informational social influence is the tendency to “accept information obtained from another as evidence about reality” (Deutsch & Gerard, 1955, p. 629). Therefore, informational social influence is a means of gaining information under circumstances where people are uncertain about their own perceptions. This is similar to Word of Mouth (Westbrook, 1987). Complimenting this is referent social influence, which works to inform opinion and assessment through group identity – people look to others to guide their own opinions within their group norms (Turner, Wetherell, & Hogg, 1989). These concepts may play an influential role in credibility.

There are trust-enhancing factors in the online environment, which users interpret when making trust-related decisions. These factors fall into several categories, including technical factors and human behavior-related factors. Technological factors may include the design, language, and reliability of a website or online forum. For example, people are attracted to a smooth, flawless website design. If they notice flaws, such as typos, it can adversely affect their decision to trust that website (Jones & Moncur, 2018). These factors are similar to the surface features of the 3S model and information characteristics mentioned above. Additionally, human behavior factors are significant to the trust and relationship formation process. These factors may include establishing rapport, transaction reliability, and customer service. They are similar to interaction characteristics previously discussed, such as benevolence, competence, predictability, and integrity. Being able to identify credible relationships and valid communication patterns may serve to enhance our confidence in assessment. Conversely, there are many relationship and communication factors that may indicate potential malicious activity.

***

#### Table of Contents
{: .no_toc}

<ul><li> <a href="/docs/A/assessing-the-credibility-of-cyber-adversaries-1/">Introduction</a></li><li> <a href="/docs/A/assessing-the-credibility-of-cyber-adversaries-2/">Literature Review and Methodology</a></li><li> <a href="/docs/A/assessing-the-credibility-of-cyber-adversaries-3/">Proposed Model for Online Adversary Credibility Assessment</a></li><li> <a href="/docs/A/assessing-the-credibility-of-cyber-adversaries-4/">Discussion</a></li><li> <a href="/docs/A/assessing-the-credibility-of-cyber-adversaries-5/">Limitations and Future Directions</a></li><li> <a href="/docs/A/assessing-the-credibility-of-cyber-adversaries-6/">Summary</a></li><li> <a href="/docs/A/assessing-the-credibility-of-cyber-adversaries-7/">Declaration of Interest Statement</a></li><li> <a href="/docs/A/assessing-the-credibility-of-cyber-adversaries-8/">References</a></li></ul>

***

</div>
