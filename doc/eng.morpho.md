# English Morpho module

This module is used for morphological tasks such as stemming, conjugation, etc.

## Accessing

```javascript
var engMorpho = new (JsLingua.getService("Morpho", "eng"))();
```

To shorten the code in the rest of this tutorial, we will define different morphological properties here:

```javascript
var Morpho = JsLingua.Cls.Morpho;
//Different global features
var F = Morpho.Feature,
    Tense = F.Tense,
    Mood = F.Mood,
    Voice = F.Voice,
    GNumber = F.Number,
    Aspect = F.Aspect,
    Gender = F.Gender,
    Person = F.Person;
```

## Conjugation

###  Conjugation forms

English module affords the following conjugation forms (we give the options of each)

#### Indicative present:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Pr, // "present"
  aspect: Aspect.S // "simple"
}
```

#### Indicative past:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Pa, // "past"
  aspect: Aspect.S // "simple"
}
```

#### Indicative future:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Fu, // "future"
  aspect: Aspect.S // "simple"
}
```

#### Indicative present perfect:

```javascript
{
  mood: Mood.Indi, // "indicative"
  tense: Tense.Pr, // "present"
  aspect: Aspect.P // "perfect"
}
```

#### Indicative past perfect:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Pa, // "past"
  aspect: Aspect.P // "perfect"
}
```

#### Indicative future perfect:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Fu, // "future"
  aspect: Aspect.P // "perfect"
}
```

#### Indicative present continuous:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Pr, // "present"
  aspect: Aspect.C // "continuous"
}
```

#### Indicative past continuous:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Pa, // "past"
  aspect: Aspect.C // "continuous"
}
```

#### Indicative future continuous:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Fu, // "future"
  aspect: Aspect.C // "continuous"
}
```

#### Indicative present perfect continuous:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Pr, // "present"
  aspect: Aspect.PC // "perfect-continuous"
}
```

#### Indicative past perfect continuous:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Pa, // "past"
  aspect: Aspect.PC // "perfect-continuous"
}
```

#### Indicative future perfect continuous:

```javascript
{
  mood: Mood.Ind, // "indicative"
  tense: Tense.Fu, // "future"
  aspect: Aspect.PC // "perfect-continuous"
}
```

### Pronouns

In English, the pronouns follow: person, number and gender properties

#### I

```javascript
{
  person:Person.F, // "first"
  number: GNumber.S // "singular"
}
```

#### We

```javascript
{
  person:Person.F, // "first"
  number: GNumber.P // "plural"
}
```

#### You

```javascript
{
  person:Person.S // "second"
}
```

#### He

```javascript
{
  person:Person.T, // "third"
  number: GNumber.S, // "singular"
  gender: Gender.M // "masculine"
}
```

#### She

```javascript
{
  person:Person.S, // "third"
  number: GNumber.S, // "singular"
  gender: Gender.F // "feminine"
}
```

#### It

```javascript
{
  person:Person.S, // "third"
  number: GNumber.S, // "singular"
  gender: Gender.N // "neuter"
}
```

#### They

```javascript
{
  person:Person.T, // "third"
  number: GNumber.P // "plural", even "dual" will work as "plural"
}
```

### Voices

English module affords passive and active voices

```javascript
{
  voice: Voice.A //"active"
}
```

```javascript
{
  voice: Voice.P //"passive"
}
```

### Negations

English module affords negative conjugation. In case of affirmative, just ignore this property

```javascript
{
  negated:1
}
```

### Conjugation examples

Let's conjugate the verb "use" in indicative mood (default), present tense, affirmative (default), active voice (default), with the pronoun "They".

Then, we conjugate it with the pronoun "He" in the past tense.

After that, we conjugate it with the pronoun "She" in the past tense, negative, passive voice

Next, we conjugate it with the pronoun "She" in the past tense, negative, passive voice, continuous aspect

```javascript
var verb = "use";
var opts = {
  //Form properties
  tense: "present",

  //negation and voice properties
  //no need (defaults)

  //pronoun properties
  person: "third",
  number: "plural"
};
console.log(engMorpho.conjugate(verb, opts));

opts.gender = "masculine";
opts.number = "singular";
opts.tense = "past";
console.log(engMorpho.conjugate(verb, opts));

opts.gender = "feminine";
opts.negated = 1;
opts.voice = "passive";
console.log(engMorpho.conjugate(verb, opts));

opts.aspect = "continuous";
console.log(engMorpho.conjugate(verb, opts));
```

The result:

```
use
used
was not used
was not being used
```

Let's conjugate the verb "take" in indicative mood (default), present tense, affirmative (default), active voice (default), with the pronoun "He".

Then, in past tense, perfect aspect

After that, in past tense, continuous perfect aspect

Then, in past tense, simple aspect

Next, in past tense, simple aspect, passive voice

Next, in future tense, passive voice

Finally, in future tense, passive voice, negative.

```javascript
var verb = "take";
var opts = {
  //Form properties
  //mood: "indicative",
  tense: "present",

  //negation and voice properties
  //no need (defaults)

  //pronoun properties
  person: "first",
  number: "singular",
  gender: "masculine"

};
console.log(engMorpho.conjugate(verb, opts));

opts.tense = "past";
opts.aspect = "perfect";
console.log(engMorpho.conjugate(verb, opts));

opts.aspect = "perfect-continuous";
console.log(engMorpho.conjugate(verb, opts));

opts.aspect = "simple";
console.log(engMorpho.conjugate(verb, opts));

opts.voice = "passive";
console.log(engMorpho.conjugate(verb, opts));

opts.tense = "future";
console.log(engMorpho.conjugate(verb, opts));

opts.negated = 1;
console.log(engMorpho.conjugate(verb, opts));
```

```
take
had taken
had been taking
took
was taken
will be taken
will not be taken
```

You can check the code here: [https://runkit.com/kariminf/jslingua-english-conjugation-test-1](https://runkit.com/kariminf/jslingua-english-conjugation-test-1)

## Stemming

### Stemming algorithms

For now, English Morpho affords two stemming Algorithms

#### English Porter stemmer

```javascript
engMorpho.setCurrentStemmer("porterStemmer");
```

#### English Lnacaster stemmer

```javascript
engMorpho.setCurrentStemmer("lancasterStemmer");
```

### Stemming examples

```javascript
console.log("=== porter Stemmer ===");
engMorpho.setCurrentStemmer("porterStemmer");
console.log(engMorpho.stem("presumably"));
console.log(engMorpho.stem("provision"));
console.log(engMorpho.stem("saying"));
console.log(engMorpho.stem("electrical"));

engMorpho.setCurrentStemmer("lancasterStemmer");
console.log(engMorpho.stem("presumably"));
console.log(engMorpho.stem("provision"));
console.log(engMorpho.stem("saying"));
console.log(engMorpho.stem("electrical"));
```
The result will be:

```
=== porter Stemmer ===
presum
provis
sai
electr
=== lancaster Stemmer ===
presum
provid
say
elect
```

You can check the code here: [https://runkit.com/kariminf/jslingua-english-stemming-test-1](https://runkit.com/kariminf/jslingua-english-stemming-test-1)

## Normalization

In English Morpho normalization, there are no options.
Its function is to return informal words to standard English.

Here, is an example of normalization

```javascript
console.log(engMorpho.normalize("ain't"));
console.log(engMorpho.normalize("innit"));
console.log(engMorpho.normalize("gonna"));
console.log(engMorpho.normalize("gotta"));
console.log(engMorpho.normalize("outta"));
console.log(engMorpho.normalize("sorta"));
console.log(engMorpho.normalize("wanna"));
console.log(engMorpho.normalize("want"));
```

The result:

```
is not
is not it
going to
have to
out of
sort of
want to
want
```

## Word conversion

### conversion algorithms

For now, English Morpho affords one conversion algorithm

#### Singular to Plural

It is not complete;

```javascript
engMorpho.setCurrentPosConverter("singularToPlural");
```

### conversion examples

```javascript
engMorpho.setCurrentPosConverter("singularToPlural");
console.log(engMorpho.convertPoS("address"));
console.log(engMorpho.convertPoS("box"));
console.log(engMorpho.convertPoS("match"));
console.log(engMorpho.convertPoS("quiz"));
console.log(engMorpho.convertPoS("ox"));

console.log(engMorpho.convertPoS("alley"));
console.log(engMorpho.convertPoS("ally"));

console.log(engMorpho.convertPoS("life"));
console.log(engMorpho.convertPoS("leaf"));
console.log(engMorpho.convertPoS("staff"));

console.log(engMorpho.convertPoS("cat"));
```

The result will be:

```
addresses
boxes
matches
quizzes
oxen
alleys
allies
lives
leaves
staffs
cats
```

[Return to index](./index.md)