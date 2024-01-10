# QA INTERNSHIP TECHNICAL TASK

## Introduction
This is a submission of completed task for QA Internship selection at Present Connection. Below you will find my take on writing a test using Cypress project, to choose and order food on Wolt.com and to deliver it to Kauno Dokas office. 

## Tools and setup
    - The test was completed using Visual Studio Code and Cypress. 
    - The object of the test is Wolt.com website and not registered user with email address theand33@armyspy.com .

## Code and explanation
The test started by opening the website and accepting optional cookies. Then I used location search window to find restaurants near Kauno Dokas and chose 'Burger' category. Since the window does not show full list of restaurants and it changes quite often, I used _force: true_ assertion to select restaurant 'Pelėdinė'. Because of the same reasons, I used _force: true_ assertion again to select 'Gringo burgeris' and add it to cart. Then I made sure the burger is in the cart and went to checkout. I was asked to login and at this point my test ended because I didn't have demo details for registered user.

```javascript
     describe('Wolt maisto užsakymas', () => {
    it('Užsakymas iš Pelėdinės', () => {
      cy.visit('https://wolt.com/en/ltu')
      .get('.sc-eec3bcfd-0').contains('Accept').click()
      .get('#front-page-input').type('Kauno dokas')
      .get('#ChIJ38lOZggi50YRWpU8_5-uibQ').click()
      .get(':nth-child(2) > .sc-147d0703-0').click()
      .get(':nth-child(2) > .sc-e4f94c87-0 > [aria-hidden="true"] > .sc-43223f4c-0 > .sc-f5bf6d34-0').click()
      .get('[data-test-id="venueCard.peledine"] > .sc-d23e97a9-43 > [aria-hidden="true"] > .sc-d23e97a9-15').click({force: true})
      .get(':nth-child(1) > .sc-ff3a5ea4-0 > .sc-ff3a5ea4-5 > :nth-child(1) > .sc-f3d0e00b-2').click({force: true})
      .get('.sc-2d01a0b8-5').click()
      .get('.sc-c1361b55-1 > :nth-child(1) > .sc-62ed5c8d-2 > .sc-62ed5c8d-3 > .sc-c1361b55-4 > .sc-c1361b55-7').click()
      .get('.sc-bd015adf-2').click()
      .get('#method-select-email').type('theand33@armyspy.com')
    }) 
  })()
```
## Conclusions
Testing Wolt.com website might be a challenging task because it is very dynamic and depending on the time of day (is the restaurant accepting orders). However some challenges can be solved with _force: true_ assertion. Also, it is best to use for the test to use demo registered user account to go through as much as possible steps.
