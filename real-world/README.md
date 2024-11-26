# The Base "Concept" Concept and Code Generation

### Written by Alexander R. Mcneilly (<mcneilly@mit.edu>)

A foundational `Concept.concept` serves as the bedrock 
upon which all other software concepts are built. This 
base Concept encapsulates the universal attributes and 
behaviors that define what it means to be a software 
concept within the system.

This helps the LLM understand the other concepts used 
for the system and makes it easier to translate it into
code. Providing a `Concept.concept` encourages the LLM 
to generate something like:

```
export abstract class Concept {
  static schema: Schema = {
    tables: {},
    views: {},
    actions: {},
  }
  static conceptName: string

  db: Store<any>

  constructor(db: Store<any>) {
    this.db = db
  }
}
```

when prompted to turn a collection of concepts from the 
concept bank into code. This way, the LLM can easily
generate code such as `class Other extends Concept {...}`
for other concepts given. This enforces a common
structure ensuring that each specialized concept adheres
to a predefined schema while retaining the flexibility 
to encapsulate unique behaviors and purposes.

Furthermore, this mirrors real-world ontological structures, 
where abstract categories underpin more specific instances.
For instance, in the ontology of wine and wineries, the 
abstract category "Wine" can have subclasses like "Red Wine"
or "White Wine," and further specific instances such as a 
particular bottle of Merlot or Chardonnay. These instances
are described by properties like flavor and body, which are
slots defined at the class level.

Consider a scenario where there is no base `Concept.concept`
in the system. Each new software concept would need to
independently define its own structure, state, and actions
without a standardized framework when translated to a tech
stack. For instance, if we told the LLM to translate both 
`Authenticating.concept` and `Profiling.concept` would have
to separately define how they handle state components like 
user data and actions like updating profiles or authenticating
sessions. This redundancy could not only leads to inconsistent 
code implementations by the LLM but also increases the 
likelihood of hallucinations, false assumptions and other
inconsistencies across the system. 

Without a base `Concept.concept`, ensuring that all concepts 
align with our overarching design principles becomes cumbersome.
If, instead of building RealWorld--which is a relatively small 
example for a comprehensive web app--, we built something more 
complex like a social network or accounting software, having 
no consistent blueprint for the LLM to translate concepts to 
code could make the code it generates from the given concepts 
less scalable and more prone to fragmentation. In contrast, 
if we include a base `Concept.concept`, each specialized 
concept inherits a common structure when translated to code, 
reducing duplication and fostering a cohesive "accent" that we
can translate between this concept markup syntax and any code 
used in a tech stack.

While one might argue that each concept should be evaluated 
based on its individual purpose and utility without relying 
on a base Concept, this perspective overlooks the benefits of 
having a standardized foundation. The base Concept does not 
constrain the unique purposes and behaviors of individual 
concepts; instead, it provides a consistent framework that 
enhances clarity and interoperability.