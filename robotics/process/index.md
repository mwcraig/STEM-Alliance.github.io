---
title: Robot Design Process
use-site-title: true
---

[![EDP](imgs/edp_s.png "EDP")](imgs/edp.png "EDP")

Example Process for Subsystem Design of a Drivetrain

<style>
* {
  box-sizing: border-box;
}

.wrapper {
  margin: 5em auto;
  max-width: 1000px;
  box-shadow: 0 0 5px 0 rgba(0, 0, 0, 0.06);
}

.cards {
  padding: 15px;
  display: flex;
  flex-flow: row wrap;
}

.card {
  margin: 15px;
  width: calc((100% / 3) - 30px);
  transition: all 0.2s ease-in-out;
}
@media screen and (max-width: 991px) {
  .card {
    width: calc((100% / 2) - 30px);
  }
}
@media screen and (max-width: 767px) {
  .card {
    width: 100%;
  }
}
.card:hover .card__inner {
  background-color: #1abc9c;
  -webkit-transform: scale(1.05);
          transform: scale(1.05);
}
.card__inner {
  width: 100%;
  padding: 30px;
  position: relative;
  cursor: pointer;
  background-color: #949fb0;
  color: #eceef1;
  font-size: 1.5em;
  text-transform: uppercase;
  text-align: center;
  transition: all 0.2s ease-in-out;
}
.card__inner:after {
  transition: all 0.3s ease-in-out;
}
.card__inner .fa {
  width: 100%;
  margin-top: .25em;
}
.card__expander {
  transition: all 0.2s ease-in-out;
  background-color: #333a45;
  width: 100%;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  text-transform: uppercase;
  color: #eceef1;
  font-size: 1.5em;
}
.card__expander .fa {
  font-size: 0.75em;
  position: absolute;
  top: 10px;
  right: 10px;
  cursor: pointer;
}
.card__expander .fa:hover {
  opacity: 0.9;
}
.card.is-collapsed .card__inner:after {
  content: "";
  opacity: 0;
}
.card.is-collapsed .card__expander {
  max-height: 0;
  min-height: 0;
  overflow: hidden;
  margin-top: 0;
  opacity: 0;
}
.card.is-expanded .card__inner {
  background-color: #1abc9c;
}
.card.is-expanded .card__inner:after {
  content: "";
  opacity: 1;
  display: block;
  height: 0;
  width: 0;
  position: absolute;
  bottom: -30px;
  left: calc(50% - 15px);
  border-left: 15px solid transparent;
  border-right: 15px solid transparent;
  border-bottom: 15px solid #333a45;
}
.card.is-expanded .card__inner .fa:before {
  content: "\f115";
}
.card.is-expanded .card__expander {
  max-height: 1000px;
  min-height: 200px;
  overflow: visible;
  margin-top: 30px;
  opacity: 1;
}
.card.is-expanded:hover .card__inner {
  -webkit-transform: scale(1);
          transform: scale(1);
}
.card.is-inactive .card__inner {
  pointer-events: none;
  opacity: 0.5;
}
.card.is-inactive:hover .card__inner {
  background-color: #949fb0;
  -webkit-transform: scale(1);
          transform: scale(1);
}

@media screen and (min-width: 992px) {
  .card:nth-of-type(3n+2) .card__expander {
    margin-left: calc(-100% - 30px);
  }

  .card:nth-of-type(3n+3) .card__expander {
    margin-left: calc(-200% - 60px);
  }

  .card:nth-of-type(3n+4) {
    clear: left;
  }

  .card__expander {
    width: calc(300% + 60px);
  }
}
@media screen and (min-width: 768px) and (max-width: 991px) {
  .card:nth-of-type(2n+2) .card__expander {
    margin-left: calc(-100% - 30px);
  }

  .card:nth-of-type(2n+3) {
    clear: left;
  }

  .card__expander {
    width: calc(200% + 30px);
  }
}
</style>

<div class="wrapper">
   <div class="cards">
      <div class="card is-collapsed">
         <div class="card__inner js-expander">
            <span>1. Define the Problem</span>
         </div>
         <div class="card__expander">
            <ul>
               <li>Questions
                  <ul>
                     <li>What is the problem?</li>
                     <li>Why is it a problem?</li>
                  </ul>
               </li>
               <li>Actions
                  <ul>
                     <li>Our existing differential tank drivetrain does not survive the rigors of multiple competition events</li>
                     <li>Instead of spending time improving other portions of the robot, we instead spend too much time making sure the drivetrain is 100% working</li>
                  </ul>
               </li>
               <li>Outcome
                  <ul>
                     <li>We need a robust, reliable, yet easily servicable differential tank drive train</li>
                  </ul>
               </li>
            </ul>
         </div>
      </div>
   </div>
</div>

## 1. Define the Problem
   - Questions
      - What is the problem?
      - Why is it a problem?
   - Actions
      - Our existing differential tank drivetrain does not survive the rigors of multiple competition events
      - Instead of spending time improving other portions of the robot, we instead spend too much time making sure the drivetrain is 100% working
   - Outcome
      - We need a robust, reliable, yet easily servicable differential tank drive train

## 2. Research Requirements and Constraints
   - Questions:
      - How have others solved similar problems?
         - Consider designs, parts, etc.
       - What external and internal restrictions are there?
         - Rulebook, cost, manufacturability, etc.
   - Actions
      - From looking at multiple successful teams' robots and discussions on CD ([1](https://www.chiefdelphi.com/forums/showthread.php?t=152211), [2](https://www.chiefdelphi.com/forums/showthread.php?t=94288), [3](https://www.chiefdelphi.com/forums/showthread.php?t=124538), we noticed most teams use aluminum box tubing, cantilever all wheels, direct drive one wheel, some form of tensioning.
      - We also found teams vary with selections of gearboxes/transmissions (gear reduction, number of motors, shifting), wheels (sizes and types), belts vs chains.
      - From the rulebook, we are restricted on components, size, weight and power.
      - From a cost standpoint, the more we make in house the cheaper the total cost, *generally*.
         - It is also easier to cut plastics then metal, and machining thinner aluminum is far easier than machining a block of aluminum.
   - Outcome
      - Recommended Requirements:
         - Easily servicable wheels, chain/belts, transmissions
         - Robust and Reliable to last more than a competition season
         - Cantilevered Wheels
         - Manufacture in house where possible
         - Use Center to Center calculators for [Belts](http://www.wcproducts.net/how-to-belts/), [Chains](http://www.botlanta.org/converters/dale-calc/sprocket.html), and [Gears](http://www.wcproducts.net/how-to-gears/) to ensure proper spacing and prevent wear
         - Use Gearbox Calculators to determine gear ratios and desired FPS - [WCProducts](http://www.wcproducts.net/how-to-drivetrain/) and [JVN Design Calculator](https://1drv.ms/x/s!AprigkKMKYgtgalQQPmc59XpZ3NQuQ)
         - Support for various wheel setups (omni/traction, 6 vs 8, etc) and various transmissions (2 vs 3 CIM, etc)

## 3. Develop Concepts

## 4. Prototype Concepts

## 5. Decision Analysis

## 6. Refine Design

## 7. Implement Final Design

## 8. Test and Analyze



<script type="text/javascript" src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
<script>
var $cell = $('.card');

//open and close card when clicked on card
$cell.find('.js-expander').click(function() {

  var $thisCell = $(this).closest('.card');

  if ($thisCell.hasClass('is-collapsed')) {
    $cell.not($thisCell).removeClass('is-expanded').addClass('is-collapsed').addClass('is-inactive');
    $thisCell.removeClass('is-collapsed').addClass('is-expanded');
    
    if ($cell.not($thisCell).hasClass('is-inactive')) {
      //do nothing
    } else {
      $cell.not($thisCell).addClass('is-inactive');
    }

  } else {
    $thisCell.removeClass('is-expanded').addClass('is-collapsed');
    $cell.not($thisCell).removeClass('is-inactive');
  }
});

//close card when click on cross
$cell.find('.js-collapser').click(function() {

  var $thisCell = $(this).closest('.card');

  $thisCell.removeClass('is-expanded').addClass('is-collapsed');
  $cell.not($thisCell).removeClass('is-inactive');

});
</script>