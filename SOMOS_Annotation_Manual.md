# The SOMOS Dataset

*Social Movements and Organized Struggle on Turkish Twitter / X*

## Annotation Manual

*Definitions and Conceptual Framework*

> Kına, Fuat; Akdeniz, Reyta; Ekmen, Helin Yaren; Cebe, Ali; Çukur, Ayşenur; Avran, Rabia; Kosova, Ayşe Merve; Gündüz, Hüsnü Berk; Karataş, Mehmet Ali; Türkoğlu, Alp Ata, 2026, “*Social Movements and Organized Struggle Dataset on Turkish Twitter/X*”, https://doi.org/10.7910/DVN/PL1DC5, Harvard Dataverse, V2.

## Contents

- [1. About This Manual](#1-about-this-manual)
- [2. The Social Movement Organization Model](#2-the-social-movement-organization-model)
- [3. Organizational Type](#3-organizational-type)
- [4. Inequality Axis](#4-inequality-axis)
- [5. Ideology](#5-ideology)
- [6. Movement Scope](#6-movement-scope)
- [7. Location](#7-location)

# 1. About This Manual

The Social Movements and Organized Struggle (SOMOS) Database is a computational inventory of social movement organizations (SMOs) active on Turkish Twitter/X, constructed on the Politus infrastructure through a theory-driven, language-model-assisted annotation pipeline. This manual documents the annotation scheme behind the dataset. It records the definition that governs which accounts enter the database, the categories used to describe each organization, and the decision rules that annotators and model prompts followed when assigning labels. Its purpose is to make the coding transparent and reproducible, so that users of the public dataset can understand how each variable was constructed and apply the same logic in extension or replication work.

All annotation in the SOMOS pipeline operates on two fields of each account, the display name and the profile description or bio. No tweet content, follower network, or external record is consulted during labelling. Where an organization is well known, background knowledge may be used to resolve or override surface cues, so that an account recognized as an established institution is coded according to what it is rather than according to the incidental wording of its bio. The underlying data is in Turkish; this manual is written in English, and category labels follow the English terms used in the released dataset.

Several conventions recur across modules and are stated once here. Most classification modules assign a primary label and, where a second category genuinely applies, an optional secondary label, so that hybrid organizations can be described without forcing a single form; a secondary label is not attached as a matter of routine. Most modules also follow an instruction-driven, stepwise decision procedure and attach a confidence level to the result, and some record a short free-text rationale. A further principle concerns branches: when an account is a branch, affiliated group, local office, or youth or student wing of a larger, already established organization, the parent organization is coded first and supplies the primary label, and the branch-specific character is recorded as the secondary label. Module-specific formulations of these conventions are given in the sections below.

# 2. The Social Movement Organization Model

The database rests on an explicit definition of its unit. Social movement organizations are organized formations that emerge and evolve from grassroots initiative, articulate public claims against prevailing authority structures through demands grounded in a principled framework, and pursue identifiable goals to realize those claims; in doing so, they coordinate collective action and sustain the continuity of an opposition over time. The detection stage translates this definition into a single binary judgement, in which an account either is or is not an SMO. Every variable documented in the sections that follow applies only to accounts that pass this stage.

## Inclusion

An account is read as an SMO when its name and description, interpreted together with any reliable background knowledge, present it as a collective actor of this kind. The decisive signals are a bottom-up or grassroots character, public claim-making directed against prevailing structures of authority rather than exercised from within them, a principled rather than purely instrumental basis for those claims, and an orientation toward sustained collective action rather than a one-off transaction. Two absolute rules protect recall at this stage: any account that signals that it is a social movement organization is never placed out of scope, and any account that signals movement, advocacy, grassroots formation, opposition, collective action, initiative, or protest of any kind is likewise retained.

## Out-of-scope accounts

Accounts that fall outside the definition are set aside through two screening labels. An account that does not belong to Turkey is labelled *nontr*. An account is labelled *other* when it belongs to an individual rather than an organization, when it is a private company or otherwise profit-based, when it publishes only news or informational content without itself representing an organization, movement, or structured group, when it is a troll or otherwise non-substantive account, or when its name and description carry too little information to support any classification. A Turkish organization that fits none of the substantive forms is also labelled *other*. These labels function as a cleaning layer rather than as descriptions of movement organizations, and they never override the two inclusion rules above.

## Screening order and calibration

The judgement follows a short procedure. The account is first checked for the country: if it is not from Turkey it is labelled nontr and no further coding follows. It is then checked against the out-of-scope definition: if it is out of scope it is labelled other and no further coding follows. Only accounts that survive both checks proceed to feature extraction. The detection stage was deliberately calibrated to favor recall over precision, because genuine SMOs are comparatively rare within the broader population of organizer accounts; tolerating a number of false positives that later stages can remove was judged more defensible than excluding true SMOs at an early and irreversible point. Prior pipeline stages had already removed private-sector, public-sector, municipality, and school or university accounts, together with the four mainstream parties of the dominant electoral blocs, while parties with predominantly grassroots characteristics were retained; these decisions define the population within which the SMO judgement is made.

# 3. Organizational Type

The organizational-type module records the form through which an account presents itself as a collective actor. It uses eight substantive categories: labor union, professional organization, party, foundation, association, student or youth organization, citizen collective, and platform or umbrella formation. A primary and an optional secondary label capture hybrid forms; where only one type fits, a single label is returned, and where two apply the result takes a primary-then-secondary form. Alongside these, the screening labels other and nontr handle accounts that are out of scope or not from Turkey, working here as a secondary cleaning mechanism for the field.

The central distinction running through the module is between institutionally established forms and informal ones. Associations, foundations, parties, labor unions, and professional organizations are institutionally established structures, whereas citizen collectives, and to a large extent platform or umbrella formations, are not. Where an account is recognized through background knowledge as an established institution, that established type governs the primary label even when the wording of the name and description points elsewhere. The branch principle applies in its fullest form here, so that a branch, affiliated group, local office, or youth or student wing takes the parent organization's type as its primary label and its own form as the secondary label. Two further patterns hold across the module: associations, parties, labor unions, and foundations rarely carry a secondary label, whereas citizen collectives, platform formations, professional organizations, and student or youth wings frequently pair with a second type; and any account organized around a specific profession or expertise must carry professional organization at least as a secondary label if it is not already primarily one.

## Labor union

All trade unions belong here, including those identifiable only by a recognized abbreviation. A genuinely institutional union is primarily a labor union. Where an account is not really a union but a looser solidarity formation of workers or pensioners, it is coded primarily as a citizen collective and secondarily as a labor union, and the question of its class character is left to the inequality-axis module; such cases are relatively rare. Because unions are organized around a profession or occupational group, they also carry professional organization as a secondary type.

## Professional organization

This category covers institutionally established bodies whose focus is a particular profession and the people who practise it, such as professional chambers and their federations. It is assigned as a primary label when the organization is built around the holders of a profession and has no wider focus. Two secondary patterns recur. Where an organization is oriented to a field of work rather than to its practitioners, professional organization is paired as a secondary label with association. Where no institutional structure exists, it is paired instead with citizen collective. All labor unions carry professional organization as a secondary label, and when a professional body is itself a registered association the association label takes primary place with professional organization as secondary.

## Party

Political parties belong here. A small number of formations that are organized entirely as a party but do not carry the word party in their name are also coded as parties on the basis of background knowledge.

## Foundation

Foundations belong here, whether signalled by the account text itself or recognized as foundations through background knowledge. As with associations, world-knowledge recognition of an established foundation sets the primary label even when the account's keywords point to another category.

## Association

Associations and non-governmental organizations with an institutionally established structure belong here. Three kinds of cue point to this label: explicit association wording in the name, registration or founding signals, or, with no keyword cue at all, recognition of the body as an established association through background knowledge, which is frequently possible from an abbreviation alone. An account known to be an established association keeps the association label even when its name gives the impression of an informal collective; it moves to citizen collective or platform or umbrella formation only when no institutionally established structure exists. When a professional body is also a registered association, the association label is primary and professional organization secondary.

## Student or youth organization

Youth and student organizations, assemblies, and groups belong here, as do university clubs and societies that have no other institutional attachment; these take the label as a primary type. As a secondary type, the label marks the youth or student wings of larger institutional bodies, and university clubs or societies tied to a parent organization.

## Citizen collective

Informal, voluntary formations that are not institutionally established belong here, including initiatives, communities, activist groups, campaigns, and public-interest formations. Many platform or umbrella formations carry citizen collective as a secondary type.

## Platform or umbrella formation

Expanded networks and multi-organizational structures such as coalitions, alliances, federations or unions of organizations, and broad platforms belong here. Informal initiatives that themselves take an umbrella form are primarily platform or umbrella formations, and where an institutional professional body functions as an umbrella structure it carries platform or umbrella formation as a secondary label.

# 4. Inequality Axis

The inequality-axis module records the principal social cleavage around which an organization frames its claims, following Walby's distinction between class, ethnicity, gender, and nation. The governing rule is one of mobilization against inequality: an axis is assigned only when an organization mobilizes against an inequality or disparity affecting a social group, and not when it merely identifies with or advocates for that group in general terms. An organization that advocates for equality in the abstract, across all axes at once rather than against a specific inequality, receives no label.

The module is multi-label and hierarchical. All four axes are weighed before any is assigned, so that the annotator does not stop at the first match but continues to test the account against each axis, and only then assigns the strongest and most central as the primary label and the next as an optional secondary label. Background knowledge may establish an axis even where the name and description contain no direct textual evidence. For branches, the axis of the parent organization is decided first with the branch set aside, and this supplies the primary label; the branch's own characteristics are then assessed, and where they relate to a different axis that axis is added as secondary, whereas if the branch shares the parent's axis a single label is returned. Where no axis applies, the organization receives no axis label.

## Class

This axis covers organizations mobilizing against inequalities tied to class position, economic conditions, or labor relations. All labor unions fall here, as do most professional organizations, the communist, socialist, and leftist parties, and accounts organized around public-sector dismissals by statutory decree. Certain bodies are exceptions: bar associations, and organizations oriented to a profession as a field rather than to its practitioners, such as a medical speciality association, are not coded as class on that basis alone. The prompt does not attempt to separate managerial or executive strata within these organizations.

## Ethnic

This axis covers organizations mobilizing against inequalities affecting ethnic minorities in Turkey, including their identity, culture, or belief. The parties and formations of the Kurdish and allied movements fall here, along with Roma, Alevi, and Dersim-centered organizing. Organizations built on Turkish ethnicity or nationalism are excluded from this axis.

## Gender

This axis covers organizations mobilizing against gender inequality and against disparities or disadvantages affecting a gender group, including women's-rights and feminist organizing, LGBTQ+ rights, and the women's branches of parties.

## Nation

This axis covers organizations mobilizing against inequalities operating at the level of states or major geopolitical blocs, such as inter-state domination and imperial occupation. Palestine, Jerusalem, and intifada solidarity are characteristic. An organization is never assigned this axis merely for being nationalist; the axis requires mobilization against the domination or occupation of a particular state.

# 5. Ideology

The ideology module infers an organization's ideological orientation from its account metadata, reading the username, display name, and bio within the Turkish sociological and political context. The coding follows Bora's conceptualization of ideology as the repertoire through which organizations define collective subjects, diagnose social problems, name adversaries, and formulate claims around state, nation, religion, class, ethnicity, gender, rights, and social order. Because it rests on public self-presentation, the label should be read as the ideological orientation an account projects online, not as a statement about internal belief, membership, or official doctrine.

The module does not rely on organization names alone but interprets meaning in context, and it proceeds through a fixed reasoning order. It first identifies the organizational type. It then extracts ideological signals from the organization's language, asking what kind of change is demanded, who is cast as the collective subject, whether workers, the nation, the community of believers, or citizens, and who or what is framed as the problem, whether the state, capital, the West, or patriarchy. It then situates those signals within the Turkish political field along the left-right, secular-religious, and Turkish-Kurdish axes. Finally it assigns the ideology that best explains the organization's political logic rather than its surface vocabulary. Each organization receives one primary ideology and, only where a strong dual structure is genuinely present, an optional secondary. Where signals are weak the more general category is preferred over the more specific, and where no ideological signal exists and the organizational type offers no clue, the account is coded Unclear.

Where more than one ideology is plausible, conflicts are resolved in a fixed order of priority:

1.  Explicit ideological identity movements take precedence, namely the Kurdish movement, feminism, LGBTQ+, Alevism, ecology, and natalism.

2.  A structural critique of the system points to socialism or Marxism, whereas system-internal, reformist change points to social democracy.

3.  A secular-republican framing points to Kemalism, whereas a framing centered on ethnic-national unity points to Turkish nationalism.

4.  Political Islam advanced as a governing project points to Islamism, whereas cultural or traditional religiosity points to conservatism.

5.  Where ambiguity remains, the less specific category is chosen.

Two further considerations qualify the coding. Labor unions require particular care, since their ideological position in Turkey varies widely; for a union the confidence level is lowered and the surrounding political context weighed more heavily. An emphasis on Turkishness is a prompt to consider Turkish nationalism. Every assigned label carries a confidence level: high for explicit ideological markers, medium for consistent but indirect signals, and low for weak or inferred ones.

## Islamism

A political project that organizes state and society according to Islamic principles, using Islam as a governing framework. Characteristic signals include appeals to the community of believers, a religious framing of politics, an anti-Western civilizational critique, and calls for a return to authentic origins.

## Conservatism

A right-leaning orientation that accepts the existing social order and anchors it in religious and traditional values, with signals such as family, tradition, homeland, and national values. Where the choice lies between Islamism and conservatism and the evidence is unclear, conservatism is chosen.

## Kemalism

The secular republican state ideology, marked by laicism, reference to Atatürk, modernization, and the republic. Kemalism is preferred over liberalism or social democracy where a secular republican framing is present. As an important exception, professional chambers and bar associations that carry no explicit secular-republican or laicist language in their bio are not defaulted to Kemalism.

## Turkish nationalism

An orientation centred on Turkish identity, unity, and sovereignty, with signals including the Turkish nation, territorial integrity, national independence, pan-Turkic unity, the idealist-nationalist tradition, and anti-Kurdish framing.

## Social democracy

A reformist, institutional, center-left orientation that seeks system-internal change and equity through social provision rather than structural, revolutionary confrontation, and with less national emphasis than the nationalist positions. Signals include social service and welfare, social justice, equality, the welfare state, and rights claimed in a non-confrontational register.

## Socialism or Marxism

A class-based critique of rights violations, working conditions, capital, state power, and imperialism, oriented to organized resistance for worker emancipation and labor rights. Signals include workers' rights, class struggle, revolutionary and anti-imperialist language, opposition to capital, anti-fascism, and a vocabulary of labor, exploitation, and inequality. In Turkey, struggles on behalf of blue-collar workers tend to follow a socialist or Marxist line.

## Liberalism

A focus on individual rights, pluralism, the rule of law, and democracy, often with an international emphasis and signals such as freedom and democratic reform.

## Kurdish movement

Organizing for Kurdish rights, identity, language, and autonomy, including regional advocacy.

## Feminism

An anti-patriarchal orientation that treats gender equality as a political project, read inclusively so as to cover organizations that work to empower women.

## LGBTQ+

A movement for the rights and recognition of diverse sexual orientations and gender identities.

## Ecology or environment

An orientation toward environmental protection and ecological justice, sometimes signalled through abbreviations.

## Natalism

A pro-family, pro-birth orientation attached to traditional gender roles.

## Alevism

An orientation centered on Alevi identity and religious recognition.

## Unclear

Reserved for accounts that carry no ideological signal and whose organizational type offers no clue. It is a residual label rather than a substantive position.

# 6. Movement Scope

The movement-scope module records the breadth and temporal horizon of an organization's claims, placing each SMO in one of three categories: programmatic, thematic, and single-demand. The classification follows a fixed procedure applied in order, stopping at the first match. A political party or any branch of one is programmatic, whatever its local or thematic appearance. Failing that, an organization whose entire purpose reduces to one specific, named, measurable outcome, and which would cease to exist once that outcome is achieved or definitively lost, is single-demand. Failing that, a think tank, research center, or academic or professional association is thematic. Finally, an organization that explicitly produces a comprehensive programme spanning several social, political, or economic domains is programmatic, and any remaining organization is thematic. The module also records a short descriptor of the domain or demand for thematic and single-demand organizations, together with a confidence level.

Several qualifications keep the scope judgement from tracking surface features. The struggle domain alone does not fix the category: an ecological, animal-rights, labor, or cultural domain becomes single-demand only when the organization's activity is anchored to one specific, named object or event, a named river, park, village, election, or local disaster, and the same domain stays thematic when the aim is open-ended. Campaign tactics are likewise not scope: a hashtag or slogan invoking a specific law is a tactic rather than evidence of single-demand purpose, and an organization working in a broad thematic domain stays thematic whatever campaign it currently runs, since the campaign is what the organization is doing while the scope is what the organization is for. A named object under threat, such as a particular dam, mine, park, or building, produces a single-demand classification when the organization exists solely to defend it. Recurring events follow thematic logic: an account that organizes an annual march or festival but represents an ongoing movement is thematic, because the event is a tactic rather than the whole purpose. Aspirational vision language, such as claims to work for a better future, for justice, or for equality, is common to almost all organizations and never counts as evidence of programmatic scope. Where the bio is missing or too short, the organization is classified from its name alone, and a place name combined with an occupational group does not by itself indicate a single demand; the default in such cases is thematic unless a specific named demand is explicit.

## Programmatic

An organization that produces a comprehensive, holistic programme aimed at transforming society, the economy, or the political system as a whole, with success measured by institutional and political restructuring and long-term hegemony-building across several domains at once. The clearest test is whether the organization has a programme, an explicit vision for reorganizing society broadly together with an action plan across domains. A broad analytical or research agenda does not qualify, a broad thematic focus such as Kurdish rights, women's rights, or labor is not in itself programmatic, and aspirational vision language is not sufficient.

## Thematic

An organization that operates within a specific struggle domain and pursues long-term structural change or representation within it, where the struggle is open-ended rather than limited to a single achievable outcome. Labor unions, the women's, Kurdish, LGBTQ+, and ecology movements, Palestine solidarity, professional associations, think tanks and research centers, academic associations, animal-rights organizations, and disaster-survivor groups organizing for ongoing rights all belong here. A thematic organization may address several sub-issues within its domain and remain thematic so long as those issues fall under one overarching domain.

## Single-demand

An organization built around a specific, concrete, and measurable demand, whose purpose is fulfilled once that demand is won or lost. Stopping a particular named project, whether a dam, a mine, or a construction, a wage or staffing claim tied to one named institution in one named negotiation, the passage or repeal of one specific named law as the organization's sole purpose, or a response confined to one disaster at one location all fall here. A union branch or workers' group qualifies only when its account is devoted entirely to one named, time-bound claim at one named employer; generic staffing or rights demands, even when expressed through insistent slogans, represent ongoing labor struggles and remain thematic.

# 7. Location

The location module is a structured information-extraction step rather than a classification. From the name and description fields it extracts every distinct mention of a Turkish administrative unit at two levels, the province or city and the district, and returns them as city-district pairs. More than one pair may be returned where an account names several places, and an empty result is returned where no location can be reliably identified.

Where a location is not stated explicitly, the city may be inferred from strong institutional cues, but only when the organization already has one certain location to anchor the inference, and a district is inferred only when the identification is highly certain. The module does not guess, so that an uncertain district is left empty and an account with no reliable location yields an empty list.
