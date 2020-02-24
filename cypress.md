API's

1. cy.visit('/wohnen');
2. cy.resetFetch();
3. cy.fetch(calls => {
      // prudsys categoryview event
      expect(calls.find('prudsys/event/categoryview?cid').length).to.be.gte(1);
4. cy.wait(1000);
5. getProductTile(0)
      .click()
      .should(() => {
        cy.fetch(calls => {
          // prudsys product view event
          expect(calls.find('prudsys/event/productview?').length).to.be.gte(1);
6. cy.queryByTestId(searchInputTestId).type('hello');
7. cy.queryByTestId(searchSubmitButtonTestId).click();
8. cy.clearLocalStorage();
9. getProductTile(0)
      .find('button')
      .click()
      .should(() => {
        cy.fetch(calls => {
          // prudsys basket event
          expect(calls.find('basket?pid')).to.have.length(1);

https://gitlab.production.moebel.de/workspace/consumer/end-user-frontend-monorepo/merge_requests/396/diffs
