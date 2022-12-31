<script>
// @ts-nocheck

   let principal = '';
   let interestRate = '';
   let years = '';

   function submitForm() {
      console.log(compoundedInterest(principal, interestRate / 100, years));
   }

   function compoundedInterest(principal, rate, year) {
      const balanceHistory = [];

      for (let i = 1; i <= year; i++) {
         const interest = principal * rate;
         principal += interest;
         balanceHistory.push({
            year: i,
            balance: principal.toFixed(2),
            interest: interest.toFixed(2),
            newPrincipal: (principal - interest).toFixed(2)
         });
      }

      return balanceHistory;
   }

</script>

<h1>Welcome to Investment Calculator</h1>
<p>Below is a calculator for estimating interest compounded investments over time. Simply enter in an amount, followed by the term (years) and the interest rate for that term.</p>
<div>
   <form on:submit|preventDefault={submitForm}>
      <div>
         <label for="principal">Amount:</label>
         <input type="number" id="principal" name="principal" bind:value={principal} min="1" max="1000000" required/>
      </div>
      <div>
         <label for="interestRate">Interest:</label>
         <input type="number" id="interestRate" name="interestRate" bind:value={interestRate} min="0" step="any" required/>
      </div>
      <div>
         <label for="years">Term:</label>
         <input type="number" id="years" name="years" bind:value={years} min="1" max="50" required/>
      </div>
      <div>
         <input type="submit" value="submit" />
      </div>
   </form>
</div>
