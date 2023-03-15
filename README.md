{
	"info": {
		"_postman_id": "93c9153e-89a9-478d-96d3-3b7ab22f867f",
		"name": "Васильев Ярослав Андреевич, ТЗ, AgentApp",
		"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json",
		"_exporter_id": "24123186"
	},
	"item": [
		{
			"name": "Getting a token",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"token\", jsonData.token);"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Content-Type",
						"value": "application/json",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"username\": \"qa@qa.qa\",\r\n    \"password\": 111\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{URL}}/v1/users/obtain-token",
					"host": [
						"{{URL}}"
					],
					"path": [
						"v1",
						"users",
						"obtain-token"
					]
				}
			},
			"response": []
		},
		{
			"name": "Driver creation",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 201\", function () {\r",
							"    pm.response.to.have.status(201);\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"first_name\", jsonData.first_name);\r",
							"\r",
							"pm.test(\"Body matches First_name: \" + pm.variables.get(\"first_name\"), function () {\r",
							"    pm.expect(pm.response.text(\"first_name\")).to.include(pm.variables.get(\"first_name\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"last_name\", jsonData.last_name);\r",
							"\r",
							"pm.test(\"Body matches Last_name: \" + pm.variables.get(\"last_name\"), function () {\r",
							"    pm.expect(pm.response.text(\"last_name\")).to.include(pm.variables.get(\"last_name\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"patronymic\", jsonData.patronymic);\r",
							"\r",
							"pm.test(\"Body matches Patronymic: \" + pm.variables.get(\"patronymic\"), function () {\r",
							"    pm.expect(pm.response.text(\"patronymic\")).to.include(pm.variables.get(\"patronymic\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"birth_date\", jsonData.birth_date);\r",
							"\r",
							"pm.test(\"Body matches Birth_date: \" + pm.variables.get(\"birth_date\"), function () {\r",
							"    pm.expect(pm.response.text(\"birth_date\")).to.include(pm.variables.get(\"birth_date\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"driving_experience_started\", jsonData.driving_experience_started);\r",
							"\r",
							"pm.test(\"Body matches Driving_experience_started: \" + pm.variables.get(\"driving_experience_started\"), function () {\r",
							"    pm.expect(pm.response.text(\"driving_experience_started\")).to.include(pm.variables.get(\"driving_experience_started\"));\r",
							"});\r",
							"\r",
							"\r",
							"\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"Driver_id\", jsonData.id);"
						],
						"type": "text/javascript"
					}
				},
				{
					"listen": "prerequest",
					"script": {
						"exec": [
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Authorization",
						"value": "Token {{token}}",
						"type": "text"
					},
					{
						"key": "Content-Type",
						"value": "application/json",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n  \"first_name\": \"Петр\",\r\n  \"last_name\": \"Ульянов\",\r\n  \"patronymic\": \"Иванович\",\r\n  \"birth_date\": \"1977-05-26\",\r\n  \"driving_experience_started\": \"1997-02-10\",\r\n  \"driver_licenses\": [\r\n    {\r\n      \"credential_type\": \"DRIVER_LICENSE\",\r\n      \"number\": \"012345\",\r\n      \"series\": \"1234\",\r\n      \"issue_date\": \"1997-02-10\"\r\n    }\r\n  ]\r\n}\r\n",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{URL}}/v1/insured_objects/drivers",
					"host": [
						"{{URL}}"
					],
					"path": [
						"v1",
						"insured_objects",
						"drivers"
					]
				}
			},
			"response": []
		},
		{
			"name": "Owner creation",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 201\", function () {\r",
							"    pm.response.to.have.status(201);\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches First_name: \" + pm.variables.get(\"first_name\"), function () {\r",
							"    pm.expect(pm.response.text(\"first_name\")).to.include(pm.variables.get(\"first_name\"));\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Last_name: \" + pm.variables.get(\"last_name\"), function () {\r",
							"    pm.expect(pm.response.text(\"last_name\")).to.include(pm.variables.get(\"last_name\"));\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Patronymic: \" + pm.variables.get(\"patronymic\"), function () {\r",
							"    pm.expect(pm.response.text(\"patronymic\")).to.include(pm.variables.get(\"patronymic\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"Person_id\", jsonData.person);"
						],
						"type": "text/javascript"
					}
				},
				{
					"listen": "prerequest",
					"script": {
						"exec": [
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Authorization",
						"value": "Token {{token}}",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n  \"first_name\": \"Петр\",\r\n  \"last_name\": \"Ульянов\",\r\n  \"patronymic\": \"Иванович\",\r\n\r\n  \"birth_date\": \"1977-05-26\",\r\n  \"credential\": [\r\n    {\r\n      \"credential_type\": \"RUSSIAN_INTERNAL_PASSPORT\",\r\n      \"issue_date\": \"1993-06-08\",\r\n      \"issue_point\": \"УФМС\",\r\n      \"issue_point_code\": \"123-456\",\r\n      \"number\": \"123456\",\r\n      \"series\": \"1234\"\r\n    }\r\n  ],\r\n  \"address\": [\r\n    {\r\n      \"address_query\": \"г Санкт-Петербург, г Ломоносов, ул Швейцарская, д 1 к 1, кв 1\",\r\n      \"address_type\": \"LEGAL_ADDRESS\",\r\n      \"region_kladr_id\": \"7800000000000\",\r\n      \"city_kladr_id\": \"7800000600000\"\r\n    },\r\n    {\r\n      \"address_query\": \"г Санкт-Петербург, г Ломоносов, ул Швейцарская, д 1 к 1, кв 1\",\r\n      \"address_type\": \"ACTUAL_ADDRESS\",\r\n      \"region_kladr_id\": \"7800000000000\",\r\n      \"city_kladr_id\": \"7800000600000\"\r\n    }\r\n  ]\r\n}\r\n",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{URL}}/v1/insured_objects/owners/natural_persons",
					"host": [
						"{{URL}}"
					],
					"path": [
						"v1",
						"insured_objects",
						"owners",
						"natural_persons"
					]
				}
			},
			"response": []
		},
		{
			"name": "Policyholder creation",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 201\", function () {\r",
							"    pm.response.to.have.status(201);\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches First_name: \" + pm.variables.get(\"first_name\"), function () {\r",
							"    pm.expect(pm.response.text(\"first_name\")).to.include(pm.variables.get(\"first_name\"));\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Last_name: \" + pm.variables.get(\"last_name\"), function () {\r",
							"    pm.expect(pm.response.text(\"last_name\")).to.include(pm.variables.get(\"last_name\"));\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Patronymic: \" + pm.variables.get(\"patronymic\"), function () {\r",
							"    pm.expect(pm.response.text(\"patronymic\")).to.include(pm.variables.get(\"patronymic\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"Policyholder_id\", jsonData.person);"
						],
						"type": "text/javascript"
					}
				},
				{
					"listen": "prerequest",
					"script": {
						"exec": [
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Authorization",
						"value": "Token {{token}}",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n  \"first_name\": \"Петр\",\r\n  \"last_name\": \"Ульянов\",\r\n  \"patronymic\": \"Иванович\",\r\n    \"gender\": \"M\",\r\n  \"birth_date\": \"1977-05-26\",\r\n  \"credential\": [\r\n    {\r\n      \"credential_type\": \"RUSSIAN_INTERNAL_PASSPORT\",\r\n      \"issue_date\": \"1993-06-08\",\r\n      \"issue_point\": \"УФМС\",\r\n      \"issue_point_code\": \"123-456\",\r\n      \"number\": \"123456\",\r\n      \"series\": \"1234\"\r\n    }\r\n  ],\r\n  \"address\": [\r\n    {\r\n      \"address_query\": \"г Санкт-Петербург, г Ломоносов, ул Швейцарская, д 1 к 1, кв 1\",\r\n      \"address_type\": \"LEGAL_ADDRESS\",\r\n      \"region_kladr_id\": \"7800000000000\",\r\n      \"city_kladr_id\": \"7800000600000\"\r\n    },\r\n    {\r\n      \"address_query\": \"г Санкт-Петербург, г Ломоносов, ул Швейцарская, д 1 к 1, кв 1\",\r\n      \"address_type\": \"ACTUAL_ADDRESS\",\r\n      \"region_kladr_id\": \"7800000000000\",\r\n      \"city_kladr_id\": \"7800000600000\"\r\n    }\r\n  ],\r\n  \"contact\": [\r\n        {\r\n            \"contact_type\": \"PHONE\",\r\n            \"data\": \"+71111111111\"\r\n        },\r\n        {\r\n            \"contact_type\": \"EMAIL\",\r\n            \"data\": \"test@mail.ru\"\r\n        }\r\n    ]\r\n}\r\n",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{URL}}/v1/insured_objects/insurants/natural_persons",
					"host": [
						"{{URL}}"
					],
					"path": [
						"v1",
						"insured_objects",
						"insurants",
						"natural_persons"
					]
				}
			},
			"response": []
		},
		{
			"name": "Car creation",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 201\", function () {\r",
							"    pm.response.to.have.status(201);\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"car_model_id\", jsonData.car_model_id);\r",
							"\r",
							"pm.test(\"Body matches Car_model_id: \" + pm.variables.get(\"car_model_id\"), function () {\r",
							"    pm.expect(pm.response.text(\"car_model_id\")).to.include(pm.variables.get(\"car_model_id\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"vin_number\", jsonData.vin_number);\r",
							"\r",
							"pm.test(\"Body matches Vin_number: \" + pm.variables.get(\"vin_number\"), function () {\r",
							"    pm.expect(pm.response.text(\"vin_number\")).to.include(pm.variables.get(\"vin_number\"));\r",
							"});\r",
							"\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"Car_id\", jsonData.id);"
						],
						"type": "text/javascript"
					}
				},
				{
					"listen": "prerequest",
					"script": {
						"exec": [
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Authorization",
						"value": "Token {{token}}",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n  \"car_model_id\": 864026180,\r\n  \"vin_number\": \"WAUZZZ8T4BA037241\",\r\n  \"manufacturing_year\": 2010,\r\n  \"max_mass\": 2000,\r\n  \"engine_power\": 211.0,\r\n  \"number_plate\": \"Р904МХ178\",\r\n  \"credential\": [\r\n    {\r\n      \"credential_type\": \"VEHICLE_REGISTRATION\",\r\n      \"issue_date\": \"2010-11-01\",\r\n      \"number\": \"267461\",\r\n      \"series\": \"78УН\"\r\n    }\r\n\r\n  ]\r\n}\r\n",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{URL}}/v3/insured_objects/cars",
					"host": [
						"{{URL}}"
					],
					"path": [
						"v3",
						"insured_objects",
						"cars"
					]
				}
			},
			"response": []
		},
		{
			"name": "Consolidation into an “insurance object”",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 201\", function () {\r",
							"    pm.response.to.have.status(201);\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Drivers: \" + pm.variables.get(\"Driver_id\"), function () {\r",
							"    pm.expect(pm.response.text(\"drivers\")).to.include(pm.variables.get(\"Driver_id\"));\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Owner: \" + pm.variables.get(\"Person_id\"), function () {\r",
							"    pm.expect(pm.response.text(\"owner\")).to.include(pm.variables.get(\"Person_id\"));\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Car: \" + pm.variables.get(\"Car_id\"), function () {\r",
							"    pm.expect(pm.response.text(\"car\")).to.include(pm.variables.get(\"Car_id\"));\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Insurant: \" + pm.variables.get(\"Policyholder_id\"), function () {\r",
							"    pm.expect(pm.response.text(\"insurant\")).to.include(pm.variables.get(\"Policyholder_id\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"InsObj_id\", jsonData.id);"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Content-Type",
						"value": "application/json",
						"type": "text"
					},
					{
						"key": "Authorization",
						"value": "Token {{token}}",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"drivers\":[\"{{Driver_id}}\"],\r\n    \"owner\": \"{{Person_id}}\",\r\n    \"car\": \"{{Car_id}}\",\r\n    \"insurant\": \"{{Policyholder_id}}\"\r\n}"
				},
				"url": {
					"raw": "{{URL}}/v1/insured_objects/",
					"host": [
						"{{URL}}"
					],
					"path": [
						"v1",
						"insured_objects",
						""
					]
				}
			},
			"response": []
		},
		{
			"name": "Contract creation",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"valid_from\", jsonData.valid_from);\r",
							"\r",
							"pm.test(\"Body matches Valid_from: \" + pm.variables.get(\"valid_from\"), function () {\r",
							"    pm.expect(pm.response.text(\"valid_from\")).to.include(pm.variables.get(\"valid_from\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"valid_to\", jsonData.valid_to);\r",
							"\r",
							"pm.test(\"Body matches Valid_to: \" + pm.variables.get(\"valid_to\"), function () {\r",
							"    pm.expect(pm.response.text(\"valid_to\")).to.include(pm.variables.get(\"valid_to\"));\r",
							"});\r",
							"\r",
							"var jsonData = JSON.parse(responseBody);\r",
							"pm.environment.set(\"agreement_id\", jsonData.id);"
						],
						"type": "text/javascript"
					}
				},
				{
					"listen": "prerequest",
					"script": {
						"exec": [
							""
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Content-Type",
						"value": "application/json",
						"type": "text"
					},
					{
						"key": "Authorization",
						"value": "Token {{token}}",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n\t\"valid_from\": \"2023-04-09\",\r\n\t\"valid_to\": \"2024-04-08\",\r\n    \"insurance_period\": 3,\r\n    \"target_of_using\": 11,\r\n    \"drivers_ids\": [\r\n        \"{{Driver_id}}\"\r\n    ],\r\n    \"is_car_without_registration\": false,\r\n\t\"engine_power\": 211.0,\r\n\t\"has_car_trailer\": false,\r\n\t\"car_type\": \"B\",\r\n    \"owner_id\": \"{{Person_id}}\",\r\n\t\"periods\": []\r\n}"
				},
				"url": {
					"raw": "{{URL}}/v3/agreements/calculations",
					"host": [
						"{{URL}}"
					],
					"path": [
						"v3",
						"agreements",
						"calculations"
					]
				}
			},
			"response": []
		},
		{
			"name": "Contract update",
			"event": [
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches First_name: \" + pm.variables.get(\"first_name\"), function () {\r",
							"    pm.expect(pm.response.text(\"first_name\")).to.include(pm.variables.get(\"first_name\"));\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Last_name: \" + pm.variables.get(\"last_name\"), function () {\r",
							"    pm.expect(pm.response.text(\"last_name\")).to.include(pm.variables.get(\"last_name\"));\r",
							"});\r",
							"\r",
							"pm.test(\"Body matches Patronymic: \" + pm.variables.get(\"patronymic\"), function () {\r",
							"    pm.expect(pm.response.text(\"patronymic\")).to.include(pm.variables.get(\"patronymic\"));\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "PATCH",
				"header": [
					{
						"key": "Authorization",
						"value": "Token {{token}}",
						"type": "text"
					}
				],
				"body": {
					"mode": "raw",
					"raw": "{\r\n    \"insured_object\": \"{{InsObj_id}}\"\r\n}",
					"options": {
						"raw": {
							"language": "json"
						}
					}
				},
				"url": {
					"raw": "{{URL}}/v1/agreements/{{agreement_id}}",
					"host": [
						"{{URL}}"
					],
					"path": [
						"v1",
						"agreements",
						"{{agreement_id}}"
					]
				}
			},
			"response": []
		},
		{
			"name": "Getting insurance calculation",
			"event": [
				{
					"listen": "prerequest",
					"script": {
						"exec": [
							""
						],
						"type": "text/javascript"
					}
				},
				{
					"listen": "test",
					"script": {
						"exec": [
							"pm.test(\"Status code is 200\", function () {\r",
							"    pm.response.to.have.status(200);\r",
							"});"
						],
						"type": "text/javascript"
					}
				}
			],
			"request": {
				"method": "POST",
				"header": [
					{
						"key": "Authorization",
						"value": "Token {{token}}",
						"type": "text"
					},
					{
						"key": "Content-Type",
						"value": "application/json",
						"type": "text"
					}
				],
				"url": {
					"raw": "{{URL}}/v1/agreements/{{agreement_id}}/results/{{ins_company_code}}",
					"host": [
						"{{URL}}"
					],
					"path": [
						"v1",
						"agreements",
						"{{agreement_id}}",
						"results",
						"{{ins_company_code}}"
					]
				}
			},
			"response": []
		}
	],
	"event": [
		{
			"listen": "prerequest",
			"script": {
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		},
		{
			"listen": "test",
			"script": {
				"type": "text/javascript",
				"exec": [
					""
				]
			}
		}
	]
}