# Hot ShEx with Danbri

``` ShExC
PREFIX schema: <http://schema.org/> # for backwards compat esp. in JSON-LD
PREFIX sdo: <https://schema.org/>   # Declaring but not using for instance data
PREFIX techdoc: sdo:                # For using within annotations

<ValidSoClaimReview> {
  schema:url IRI ;
  schema:claimReviewed . ;
  schema:itemReviewed {
    a [schema:CreativeWork] ;
  } AND @<ItemReviewedShape> OR {
    a [schema:Claim]
  } AND @<ClaimShape> + // techdoc:strength techdoc:recommends ;
  schema:author {
    a [schema:Organization schema:Person] ;
  } AND {
      schema:name .
    | schema:url IRI // techdoc:strength techdoc:recommends %techdoc:wasm{ "is_value_url()" %} ;
  } ;
  schema:reviewRating {
    a [schema:Rating] ;
  } AND @<ReviewRatingShape> +
}
```
