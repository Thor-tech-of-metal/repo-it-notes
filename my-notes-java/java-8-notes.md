Java to study
=============


* Remove a optional using Map

final var idsOptional = Optional.of(Arrays.of("1","2"));
final var jurisdictions = idsOptional
                            .map(ids -> jurisdictionService.getAll(ids))
                            .orElseGet(jurisdictionService::getAll);


* optional  get  optional value or throw an error using orElseThrow 

val  caseType = definitionDataItem.getString(ColumnName.CASE_TYPE_ID);

val caseTypeEntityOptional = parseContext.getCaseTypes()
  .stream()
  .filter(caseTypeEntity -> caseTypeEntity.getReference().equals(caseType))
  .findAny();

 
////// code A
if (caseTypeEntityOptional.isPresent()) {
  CaseTypeLiteEntity caseTypeLiteEntity = toCaseTypeLiteEntity(caseTypeEntityOptional.get());
  categoriesEntity.setCaseType(caseTypeLiteEntity);
} else {
  throw new InvalidImportException();
}

///// code B that remplace A
val caseTypeLiteEntity  = toCaseTypeLiteEntity(caseTypeEntityOptional.orElseThrow(InvalidImportException::new));



* Java 11. isBlank() vs isEmpty()
```
public class Main 
{
    public static void main(String[] args) 
    {
        System.out.println( "ABC".isBlank() );      //false
        System.out.println( "  ".isBlank() );       //true
 
        System.out.println( "ABC".isEmpty() );      //false
        System.out.println( "  ".isEmpty() );       //false
    }
}
````

List 
=====

* Quick notation from Arrays
```
import java.util.Arrays;
Arrays.asList("serviceName")
```


List to Maps
============

*   Collectors.toMap
```
public Map<String, String> listToMap(List<Book> books) {
    return books.stream().collect(Collectors.toMap(Book::getIsbn, Book::getName));
}
```

* Using pairs com.microsoft.applicationinsights.boot.dependencies.apachecommons.lang3.tuple;
  
```
private Map<String, String> createCaseTypeCategoryIdPair(List<DefinitionDataItem> categoryItems) {

  return categoryItems.stream().map(p->
    Pair.of(p.getString(ColumnName.CASE_TYPE_ID), p.getString(ColumnName.CATEGORY_ID)))
    .collect(Collectors.toMap(Pair::getKey,Pair::getValue));

}
```


Example of Optional get or error
================================
```
Optional<HearingResponseEntity> hearingResponse = hearingEntity.getHearingResponseForLatestRequest();
return getLowestDate(hearingResponse.orElseThrow(() -> new BadRequestException("some error"))));

public LocalDate getLowestDate(HearingResponseEntity hearingResponse) {
  //something
}
```

Inmutable initialization with lombok
======================================

```
Optional<TranslationUploadEntity> translationUploadEntity = hasAnyTranslations(dictionaryRequest)
            ? Optional.of(new TranslationUploadEntity())
            : Optional.empty();
```

```
val newEntity = isManageTranslationRole
           ? dictionaryMapper.modelToEntityWithTranslationUploadEntity(currentPhrase, currentUserId)
           : dictionaryMapper.modelToEntityWithoutTranslationPhrase(currentPhrase);
       dictionaryRepository.save(newEntity);


 where
 Optional<TranslationUploadEntity> modelToEntityWithTranslationUploadEntity(){
    Optional.of(new TranslationUploadEntity())
 }

 Optional<TranslationUploadEntity> modelToEntityWithoutTranslationPhrase(){
    Optional.empty();
 }

```
