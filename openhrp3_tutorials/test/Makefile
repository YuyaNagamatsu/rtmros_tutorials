all: test_samplerobot.py test_barrett-wam.py


samplerobot.l:
	rosrun openhrp3 export-collada -i `rospack find openhrp3`/share/OpenHRP-3.1/sample/model/sample1.wrl -o samplerobot.dae
	rosrun euscollada collada2eus samplerobot.dae samplerobot.l || echo "ok"

test_samplerobot.py: samplerobot.l gen-testcode.l
	rosrun euslisp irteusgl samplerobot.l gen-testcode.l "(gen-testcode (samplerobot) '(:waist_link1_lk :waist_link2_lk :waist_link3_lk :larm_link1_lk :larm_link2_lk :larm_link3_lk :larm_link4_lk :larm_link5_lk :larm_link6_lk :larm_link7_lk :rarm_link1_lk :rarm_link2_lk :rarm_link3_lk :rarm_link4_lk :rarm_link5_lk :rarm_link6_lk :rarm_link7_lk :lleg_link1_lk :lleg_link2_lk :lleg_link3_lk :lleg_link4_lk :lleg_link5_lk :lleg_link6_lk :rleg_link1_lk :rleg_link2_lk :rleg_link3_lk :rleg_link4_lk :rleg_link5_lk :rleg_link6_lk) \"openhrp3\" \"share/OpenHRP-3.1/sample/model/sample1.wrl\")" "(exit)"
	chmod u+x $@

barrett-wam.l:
	rosrun euscollada collada2eus barrett-wam.zae barrett-wam.l || echo "ok"

test_barrett-wam.py: barrett-wam.l gen-testcode.l
	rosrun euslisp irteusgl barrett-wam.l gen-testcode.l "(gen-testcode (wam7) '(:wam1_lk :wam2_lk :wam3_lk :wam4_lk :wam5_lk :wam6_lk :wam7_lk) \"openhrp3_tutorials\" \"test/barrett-wam.zae\")" "(exit)"
	chmod u+x $@

clean:
	rm -fr *.dae samplerobot.l test_samplerobot.py barrett-wam.l test_barrett-wam.py barrett-wam.zae


