# Document
Cocos-BCX document.
{
	"name": "artifacts_default",
	"version": "1.0.0",
	"client": {
		"tlsEnable": true,
		"adminUser": "admin",
		"adminPassword": "adminpw",
		"enableAuthentication": false,
		"organization": "Org1MSP",
		"adminCredential": {
			"id": "exploreradmin",
			"password": "exploreradminpw"
	    },
		"connection": {
			"timeout": {
				"peer": {
					"endorser": "300"
				},
				"orderer": "300"
			}
		}
	},
	"channels": {
		"mychannel": {
			"peers": {
				"peer0.org1.example.com": {}
			},
			"connection": {
				"timeout": {
					"peer": {
						"endorser": "6000",
						"eventHub": "6000",
						"eventReg": "6000"
					}
				}
			}
		}
	},
	"organizations": {
		"Org1MSP": {
			"mspid": "Org1MSP",
			"adminPrivateKey": {
				"path": "/tmp/crypto/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/keystore/5890f0061619c06fb29dea8cb304edecc020fe63f41a6db109f1e227cc1cb2a8_sk"
			},
			"peers": ["peer0.org1.example.com,peer1.org1.example.com"],
			"signedCert": {
				"path": "/tmp/crypto/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/signcerts/Admin@org1.example.com-cert.pem"
			}
		}
	},
	"peers": {
		"peer0.org1.example.com": {
			"tlsCACerts": {
				"path": "/tmp/crypto/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/tls/ca.crt"
			},
			"url": "grpcs://peer0.org1.example.com:7051",
			"eventUrl": "grpcs://peer0.org1.example.com:7053",
			"grpcOptions": {
				"ssl-target-name-override": "peer0.org1.example.com"
			}
		}
	}
}
