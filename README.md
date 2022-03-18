# Student Grades
<br>
<section class="body">
  <div class="row">
    <form name="myform">
      <div class="one-half column">
        <table>
          <thead>
            <tr>
              <th style="text-align:left">Your Grade Calculator</th>
              <th style="text-align:center">Grades</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td style="text-align:left">Homework Average:</td>
              <td style="text-align:center">
                <input type="number" name="homework" min="0" max="100" step="1" required="">
              </td>
            </tr>
            <tr>
              <td style="text-align:left">Mid-Term Exam:</td>
              <td style="text-align:center">
                <input type="number" name="midterm" min="0" max="100" step="1" required="">
              </td>
            </tr>
            <tr>
              <td style="text-align:left">Final Exam:</td>
              <td style="text-align:center">
                <input type="number" name="final" min="0" max="100" step="1" required="">
              </td>
            </tr>
            <tr>
              <td style="text-align:left">Participation:</td>
              <td style="text-align:center">
                <input type="number" name="participation" min="0" max="100" step="1" required="">
              </td>
            </tr>
            <tr>
              <td style="text-align:left">
                <strong>Final Average</strong>
              </td>
              <td style="text-align:center">
              <div id="finalaverage"></div>
              </td>
            </tr>
            <tr>
              <td style="text-align:left">
                <strong>Final Letter Grade</strong>
              </td>
              <td style="text-align:center">
                <div id="finalletter"></div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
      <div class="one-half column">
        <br>
        <br>
        <span class="button-row">
          <input type="button" class="button-primary" onclick="average()" value="Submit">
          <input type="reset" value="Reset" id="reset">
        </span>
        <br>
        <textarea rows="4" cols="28" name="result" id="results"></textarea>
      </div>
    </form>
  </div>
</section>
<br>
<script>
  const displayResults=(e="",t="",a="")=>{document.getElementById("results").textContent=e,document.getElementById("finalaverage").textContent=t,document.getElementById("finalletter").textContent=a};function average(){let e={homework:parseInt(document.forms.myform.elements.homework.value),midterm:parseInt(document.forms.myform.elements.midterm.value),final:parseInt(document.forms.myform.elements.final.value),participation:parseInt(document.forms.myform.elements.participation.value),average:()=>Math.round(.5*e.homework+.2*e.midterm+.2*e.final+.1*e.participation),letter:()=>e.average()>=90?"A":e.average()>=80?"B":e.average()>=70?"C":e.average()>=80?"D":"F",result:()=>e.average()<70?"Student must retake the course.":""};Number.isNaN(e.homework)||Number.isNaN(e.midterm)||Number.isNaN(e.final)||Number.isNaN(e.participation)||0>e.homework||e.homework>100||0>e.midterm||e.midterm>100||0>e.final||e.final>100||0>e.participation||e.participation>100?displayResults("Invalid input! Please enter integers between 0 and 100."):displayResults(e.result(),String(e.average()),e.letter())}document.getElementById("reset").addEventListener("click",(()=>{displayResults()}))
  </script>
