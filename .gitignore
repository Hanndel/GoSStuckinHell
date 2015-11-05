if GetObjectName(GetMyHero()) ~= "Ziggs" then return end

require("Inspired")

StickyBombs = Menu("Ziggs", "Ziggs")
StickyBombs:SubMenu("Combo", "Combo")
StickyBombs.Combo:Boolean("Q", "Use Q", true)
StickyBombs.Combo:Boolean("W", "Use W", false)
StickyBombs.Combo:Boolean("E", "Use E", true)
StickyBombs.Combo:Boolean("R", "Use R", true)

StickyBombs:SubMenu("Misc", "Misc")
StickyBombs.Misc:Boolean("KS", "Killsteal", true)

OnTick(function(myHero)
	if not IsDead(myHero) then
		local unit = GetCurrentTarget()
		KS()
		Combo(unit)
	end
end)

function Combo(unit)
	if IOW:Mode() == "Combo" then
			
			--Q Logic
			if StickyBombs.Combo.Q:Value() and CanUseSpell(myHero,_Q) == READY and ValidTarget(unit, GetCastRange(myHero,_Q)) then
				local QPred = GetPredictionForPlayer(GetOrigin(myHero),unit,GetMoveSpeed(unit),1700,100,GetCastRange(myHero,_Q),150,false,true)
				if QPred.HitChance == 1 then				
					CastSkillShot(_Q,QPred.PredPos.x,QPred.PredPos.y,QPred.PredPos.z)
				end
			end
			
			--E Logic
			if StickyBombs.Combo.E:Value() and CanUseSpell (myHero,_E) == READY and ValidTarget(unit, GetCastRange(myHero,_E)) then
				local EPred = GetPredictionForPlayer(GetOrigin(myHero),unit,GetMoveSpeed(unit),1300,100,GetCastRange(myHero,_E),325,false,true)
				if EPred.HitChance == 1 then
					CastSkillShot(_E,EPred.PredPos.x,EPred.PredPos.y,EPred.PredPos.z)
				end
			end
			
			--W Logic
			if StickyBombs.Combo.W:Value() and CanUseSpell(myHero,_W) == READY and ValidTarget(unit,GetCastRange(myHero,_W)) then
				local WPred = GetPredictionForPlayer(GetOrigin(myHero),unit,GetMoveSpeed(unit)*1.2,1500,100,GetCastRange(myHero,_W),325,false,true)
				if WPred.HitChance == 1 then
					CastSkillShot(_W,WPred.PredPos.x,WPred.PredPos.y,WPred.PredPos.z)
				end		
			end
			
			--Kill Ult
			local RDmg= 100+100*GetCastLevel(myHero,_R)+GetBonusAP(myHero)*0.72
			
			if StickyBombs.Combo.R:Value() and CanUseSpell(myHero,_R) == READY and ValidTarget(unit,GetCastRange(myHero,_R)) and CalcDamage(myHero, unit, 0, RDmg)>GetCurrentHP(unit) then
				local RPred = GetPredictionForPlayer(GetOrigin(myHero),unit,GetMoveSpeed(unit),2000,550,GetCastRange(myHero,_R),550,false,true)
				if RPred.HitChance == 1 then
					CastSkillShot(_R,RPred.PredPos.x,RPred.PredPos.y,RPred.PredPos.z)
				end	
			end			
	end
end

function KS()
	local RDmg= 100+100*GetCastLevel(myHero,_R)+GetBonusAP(myHero)*0.72
	for _,Enemy in pairs(GetEnemyHeroes()) do
		--R KS
		if StickyBombs.Misc.KS:Value() and CanUseSpell(myHero,_R) == READY and ValidTarget(Enemy,GetCastRange(myHero,_R)) and CalcDamage(myHero, Enemy, 0, RDmg)>GetCurrentHP(Enemy) then
			local RPred = GetPredictionForPlayer(GetOrigin(myHero),Enemy,GetMoveSpeed(Enemy),2000,550,GetCastRange(myHero,_R),550,false,true)
			if RPred.HitChance == 1 then
				CastSkillShot(_R,RPred.PredPos.x,RPred.PredPos.y,RPred.PredPos.z)
			end	
		end	
	end
end	

print("Welcome To |ELO|Hell| Credits to Logge <3 for his time")
