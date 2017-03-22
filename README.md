using UnityEngine;
using System.Collections;

public class basic_con2 : MonoBehaviour {

	public bool goToWork;
	public GameObject mover;
	public GameObject finishPos;
	public GameObject[] eneimes; 
	Vector3 moverOrigin;
	public Vector3 keyPos;
	bool haskey;

	public Renderer rend;


	void Start () {

	}

	// Update is called once per frame
	void Update () {
		Debug.Log ("game object is at ... " + mover.transform.position);
		if (Input.GetKeyDown ("left")) {
			mover.transform.position += new Vector3 (-1, 0, 0);
			rend.material.color = Color.red;
		}
		if (Input.GetKeyDown ("right")) {
			mover.transform.position += new Vector3 (1, 0, 0);
		}
		if (Input.GetKeyDown ("up")) {
			mover.transform.position += new Vector3 (0, 0, 1);
		}
		if (Input.GetKeyDown ("down")) {
			mover.transform.position += new Vector3 (0, 0, -1);
		}

		if (mover.transform.position.z < -9) {
			mover.transform.position = new Vector3 (0, 0, 0);
		}
		if (mover.transform.position.z > 9) {
			mover.transform.position = new Vector3 (0, 0, 0);
		}
		if (mover.transform.position.x < -9) {
			mover.transform.position = new Vector3 (0, 0, 0);
		}
		if (mover.transform.position.x > 9) {
			mover.transform.position = new Vector3 (0, 0, 0);
		}

		for (int i = 0; i < eneimes.Length; i++) {
			if (eneimes [i].transform.position.z < 6) {
				eneimes [i].transform.position = new Vector3 (0, 0, .2f);
			} else {
				eneimes [i].transform.position = new Vector3 (eneimes [i].transform.position.x, eneimes [i].transform.position.y, -9);

				if (mover.transform.position == eneimes[i].transform.position) { 
					mover.transform.position = moverOrigin;
					haskey = false;
					keyPos = new Vector3 (Random.Range (-3, 0), 0, 0);
				}
			}
		}
	}
	}
