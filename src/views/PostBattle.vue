<template>
  <div>
    <h1>4. Post-Battle (Pg.119)</h1>

    <div class="row row-cols-1 row-cols-md-3 rows-cols-lg-4 g-4">
      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>1. Resolve Rival Status</h5>
          </div>
          <div class="card-body">
            <div class="col d-flex flex-column">
              <p>
                Skip for <strong>Invasion battle</strong> or
                <strong>Roving Threats</strong> enemies.
              </p>
              <div class="input-group mb-3 input-group-sm">
                <div class="input-group-text">
                  <input
                    class="form-check-input mt-0"
                    type="checkbox"
                    value=""
                    aria-label="Held the field"
                    v-model="battle.heldTheField"
                  />
                </div>
                <span class="input-group-text" id="savvy-addon"
                  >Held the Field</span
                >
              </div>
              <div
                class="input-group mb-3 input-group-sm"
                v-if="battle.heldTheField"
              >
                <div class="input-group-text">
                  <input
                    class="form-check-input mt-0"
                    type="checkbox"
                    value=""
                    aria-label="Existing Rival"
                    v-model="battle.existingRival"
                  />
                </div>
                <span class="input-group-text" id="savvy-addon"
                  >Existing Rival</span
                >
              </div>
              <div
                class="input-group mb-3 input-group-sm"
                v-if="battle.existingRival"
              >
                <div class="input-group-text">
                  <input
                    class="form-check-input mt-0"
                    type="checkbox"
                    value=""
                    aria-label="Existing Rival"
                    v-model="battle.killedUniqueIndividual"
                  />
                </div>
                <span class="input-group-text" id="savvy-addon"
                  >Killed Unique Individual</span
                >
              </div>
              <div
                class="input-group mb-3 input-group-sm"
                v-if="battle.existingRival"
              >
                <div class="input-group-text">
                  <input
                    class="form-check-input mt-0"
                    type="checkbox"
                    value=""
                    aria-label="Existing Rival"
                    v-model="battle.trackedDownRival"
                  />
                </div>
                <span class="input-group-text" id="savvy-addon"
                  >Tracked down the rival</span
                >
              </div>

              <div class="mb-3 text-center" v-if="battle.heldTheField">
                <i
                  class="fas fa-dice me-1 mt-1 d-print-none fa-2x"
                  @click="resolveRivalsRoll()"
                ></i>
                <label>{{ getFindPatronResult }}</label>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>2. Resolve Patron Status</h5>
          </div>
          <div class="card-body">
            <div class="h6">Upkeep</div>
            <p class="card-text">Patron</p>
          </div>
        </div>
      </div>

      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>3. Determine Quest Progress</h5>
          </div>
          <div class="card-body">
            <p class="card-text"></p>
          </div>
        </div>
      </div>

      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>4. Get Paid</h5>
          </div>
          <div class="card-body"></div>
        </div>
      </div>

      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>
              5. Battlefield Finds
              <i
                class="fas fa-dice pe-auto d-print-none"
                @click="resolveAnyRumors()"
              ></i>
            </h5>
          </div>
          <div class="card-body">
            <div class="input-group mb-3 input-group-sm">
              <span class="input-group-text" id="savvy-addon"
                >Total Rumors (Pg.85)</span
              >
              <input
                type="number"
                class="form-control"
                placeholder="0"
                aria-label="savvy"
                aria-describedby="savvy-addon"
                min="0"
                v-model.number="resolveRumors.totalRumors"
              />
            </div>
            <label>{{ getResolveRumorsResults }}</label>
          </div>
        </div>
      </div>

      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>6. Check for Invasion!</h5>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>7. Gather the Loot</h5>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>8. Determine Injuries and Recovery</h5>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>9. Experience and Character Upgrades</h5>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>10. Invest in Advanced Training</h5>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>11. Purchase Items</h5>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>12. Roll for a Campaign Event</h5>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>13. Roll for a Character Event</h5>
          </div>
        </div>
      </div>
      <div class="col">
        <div class="card">
          <div class="card-header bg-light border-success">
            <h5>14. Check for Galactic War Progress</h5>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { FPFHTables } from "../js/tables.js";
import { DataStore } from "@aws-amplify/datastore";
import { Crew, CrewMember } from "../models";

export default {
  name: "PostBattle",
  components: {},
  mounted() {
    this.fetchCrews();
  },
  data() {
    return {
      // new
      battle: {
        heldTheField: false,
        existingRival: false,
      },
      resolveRivals: {
        hasRolled: false,
        roll: 0,
      },
      resolveRumors: {
        hasRolled: false,
        roll: 0,
      },
      // old
      jobOffer: [],
      crewTasks: [
        {
          label: "Patron",
          task: "patron",
          numCrew: 0,
          contacts: 0,
          credits: 0,
          roll: 0,
          hasRolled: false,
        },
        { label: "Train", task: "train" },
        {
          label: "Trade",
          task: "trade",
          items: [],
          rolls: 0,
          hasRolled: false,
        },
        {
          label: "Recruit",
          task: "recruit",
          roll: 0,
          numCrew: 0,
          hasRolled: false,
        },
        {
          label: "Explore",
          task: "explore",
          items: [],
          rolls: 0,
          hasRolled: false,
        },
        {
          label: "Track",
          task: "track",
          roll: 0,
          numCrew: 0,
          credits: 0,
          hasRolled: false,
        },
        {
          label: "Repair",
          task: "repair",
          roll: 0,
          savvy: 0,
          isEngineer: false,
          credits: 0,
          hasRolled: false,
        },
        { label: "Decoy", task: "decoy", number: 0 },
      ],
      checkRivals: {
        totalRivals: 0,
        totalDecoys: 0,
        roll: 0,
        hasRolled: false,
      },
      worldTrait: {
        CorporateState: false,
        TechnicalKnowledge: false,
        EasyRecruiting: false,
      },
    };
  },
  tables: new FPFHTables(),
  computed: {
    username: function () {
      return this.$store.state.user.username;
    },
    getFindPatronResult() {
      if (!this.crewTasks.find((t) => t.task === "track").hasRolled) {
        return "Waiting on roll...";
      }

      const roll = this.crewTasks.find((t) => t.task === "track").roll;
      const numCrew = this.crewTasks.find((t) => t.task === "track").numCrew;
      const credits = this.crewTasks.find((t) => t.task === "track").credits;
      const finalResult = roll + numCrew + credits;

      let result = `Rolled ${roll} (+ ${numCrew} crew + ${credits} credits): `;
      if (finalResult >= 6) {
        result += "Found a Rival.";
      } else {
        result += "Failed!";
      }
      return result;
    },

    getTrackResults() {
      if (!this.crewTasks.find((t) => t.task === "track").hasRolled) {
        return "Waiting on roll...";
      }

      const roll = this.crewTasks.find((t) => t.task === "track").roll;
      const numCrew = this.crewTasks.find((t) => t.task === "track").numCrew;
      const credits = this.crewTasks.find((t) => t.task === "track").credits;
      const finalResult = roll + numCrew + credits;

      let result = `Rolled ${roll} (+ ${numCrew} crew + ${credits} credits): `;
      if (finalResult >= 6) {
        result += "Found a Rival.";
      } else {
        result += "Failed!";
      }
      return result;
    },
    getRepairResults() {
      const repair = this.crewTasks.find((t) => t.task === "repair");
      if (!repair.hasRolled) {
        return "Waiting on roll...";
      }
      const roll = repair.roll;
      const credits = repair.credits;
      const isEngineer = repair.isEngineer ? 1 : 0;
      const techKnowledge = this.worldTrait.TechnicalKnowledge ? 1 : 0;
      const savvy = repair.savvy;
      const spareParts = this.SpareParts ? 1 : 0;
      const repairBot = this.RepairBot ? 1 : 0;
      const finalResult =
        roll +
        savvy +
        isEngineer +
        techKnowledge +
        spareParts +
        repairBot +
        credits;

      let result = `Result ${finalResult}: `;
      if (roll == 1) {
        result = "Rolled natural 1. Item destroyed!";
        if (this.SpareParts) {
          result += " Spare parts used up.";
        }
      } else {
        if (finalResult >= 6) {
          result += "Repair successful!";
        } else {
          result += "Failed!";
        }
      }
      result += `<div class='small'>
        (roll ${roll}
        + ${savvy} savvy 
        + ${isEngineer} engineer 
        + ${techKnowledge} technical knowledge 
        + ${repairBot} repair bot
        + ${spareParts} spare parts
        + ${credits} credits)
      </div>`;
      return result;
    },
    getResolveRumorsResults() {
      if (!this.resolveRumors.hasRolled) {
        return "Waiting on roll...";
      }
      const roll = this.resolveRumors.roll;

      let result = `Rolled ${roll}: `;
      if (roll <= this.resolveRumors.totalRumors) {
        result += "Quest Found!";
      } else {
        result += "No quest found.";
      }
      return result;
    },
    getCheckForRivalsResults() {
      if (!this.checkRivals.hasRolled) {
        return "Waiting on roll...";
      }
      const roll = this.checkRivals.roll;
      const decoys = this.checkRivals.totalDecoys;
      const finalResult = roll + decoys;

      let result = `Rolled ${roll} (+ ${decoys} decoys): `;
      if (finalResult <= this.checkRivals.totalRivals) {
        result += "A rival has tracked you down!";
      } else {
        result += "No rivals have found you.";
      }
      return result;
    },
  },
  methods: {
    resolveRivalsRoll() {
      alert("anti");
    },
    async fetchCrews() {
      this.crews = await DataStore.query(Crew, (c) =>
        c.user("eq", this.username)
      );
      this.crewMembers = await DataStore.query(CrewMember, (c) =>
        c.user("eq", this.username)
      );
    },
    rerollTable(table) {
      const roll = this.$options.tables.GetFullTableResult(table);
      let jobLine = this.jobOffer.find((o) => o.id === table);
      jobLine.result = roll[0];

      this.$root.showUserMsg(`Re-rolled ${table}`);
    },
    rollDice(dice) {
      const roll = this.$options.tables.Roll(dice);
      this.$root.showUserMsg(`Rolled ${dice} - 🎲 ${roll}`);
      return roll;
    },
    rollOnDangerPay(rollBonus) {
      let dangerPayTable = this.$options.tables.tables.dangerpay.tables.default;
      const dangerRoll = this.rollDice("1d10") + (rollBonus ? rollBonus : 0);
      let result = null;
      switch (dangerRoll) {
        case 1:
        case 2:
        case 3:
        case 4:
          result = dangerPayTable[0];
          break;
        case 5:
        case 6:
        case 7:
        case 8:
          result = dangerPayTable[1];
          break;
        case 9:
          result = dangerPayTable[2];
          break;
        default:
          result = dangerPayTable[3];
      }
      return result.label;
    },
    rollOnTimeFrame(rollBonus) {
      let timeFrameTable = this.$options.tables.tables.timeframe.tables.default;
      const timeFrameRoll = this.rollDice("1d10") + (rollBonus ? rollBonus : 0);
      let result = null;
      switch (timeFrameRoll) {
        case 1:
        case 2:
        case 3:
        case 4:
        case 5:
          result = timeFrameTable[0];
          break;
        case 6:
        case 7:
          result = timeFrameTable[1];
          break;
        case 8:
        case 9:
          result = timeFrameTable[2];
          break;
        default:
          result = timeFrameTable[3];
      }
      return result.label;
    },
    findPatron() {
      let patron = this.crewTasks.find((t) => t.task === "patron");
      if (patron.numCrew == 0) {
        return;
      }

      const dice = `1d6`;
      let roll = this.rollDice(dice);
      if (this.worldTrait.CorporateState) {
        roll = roll + 2;
      }
      patron.roll = roll;
      patron.hasRolled = true;
    },
    findTrade() {
      let trade = this.crewTasks.find((t) => t.task === "trade");
      let numRolls = trade.rolls;

      if (numRolls > 0) {
        let items = [];
        for (var i = 0; i < numRolls; i++) {
          let result = this.$options.tables.GetTableResult("traderesult");
          items.push(result);
        }
        trade.items = items;
        trade.hasRolled = true;
      }
    },
    findRecruit() {
      let recruit = this.crewTasks.find((t) => t.task === "recruit");
      if (recruit.numCrew == 0) {
        return;
      }

      const dice = `1d6`;
      let roll = this.rollDice(dice);
      if (this.worldTrait.easyRecruit) {
        roll++;
      }

      recruit.roll = roll;
      recruit.hasRolled = true;
    },
    findExploration() {
      let explore = this.crewTasks.find((t) => t.task === "explore");
      let numRolls = explore.rolls;

      if (numRolls > 0) {
        let items = [];
        for (var i = 0; i < numRolls; i++) {
          let result = this.$options.tables.GetTableResult("exploration");
          items.push(result);
        }
        explore.items = items;
        explore.hasRolled = true;
      }
    },
    trackRival() {
      let track = this.crewTasks.find((t) => t.task === "track");
      if (track.numCrew == 0) {
        return;
      }

      const dice = `1d6`;

      const roll = this.rollDice(dice);
      track.roll = roll;
      track.hasRolled = true;
    },
    repairItem() {
      let repair = this.crewTasks.find((t) => t.task === "repair");
      const dice = `1d6`;

      let roll = this.rollDice(dice);
      if (this.worldTrait.TechnicalKnowledge) {
        roll++;
      }

      repair.roll = roll;
      repair.hasRolled = true;
    },
    resolveAnyRumors() {
      const dice = `1d6`;

      const roll = this.rollDice(dice);
      this.resolveRumors.roll = roll;
      this.resolveRumors.hasRolled = true;
    },
    checkForRivals() {
      const dice = `1d6`;

      const roll = this.rollDice(dice);
      this.checkRivals.roll = roll;
      this.checkRivals.hasRolled = true;
    },
  },
};
</script>

<style scoped>
label {
  font-weight: 700;
}

.col {
  page-break-inside: avoid;
}

input[type="number"] {
  text-align: center;
}
</style>
