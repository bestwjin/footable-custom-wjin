# footable-custom-wjin
Customizing footable

footable library : https://fooplugins.github.io/FooTable/
를 입맛에 맞게 커스터마이징 함.


테이블 컬럼에 input이나 select가 있을경우 filtering 이 되지 않는 현상 처리.
가져온 Cell의 하위에 select나 input이 존재하면 각각 selected된 value의 
html값이나 value값을 추출하여 필터목록에 adding함.

4668라인 즈음.

"
if (F.is.element(valueOrElement) || F.is.jq(valueOrElement)){
  var data = $(valueOrElement).data('filterValue');

  // 만약 셀에 input이나 select가 있을경우의 처리.
  var selobj = $(valueOrElement).find("select option:selected");
  var inputobj = $(valueOrElement).find("input[type=text]");

  if(inputobj.val() != "") $(valueOrElement).text(inputobj.val());
  if(selobj.val() != "") $(valueOrElement).text(selobj.html());

  return F.is.defined(data) ? ''+data : $(valueOrElement).text();
}
"
