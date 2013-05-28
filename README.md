angular-CapturePlus
=========

angular-CapturePlus enables [Capture Plus](http://www.postcodeanywhere.co.uk/retail-uk-feb-13/) to work in conjunction with [AngularJS](http://angularjs.org).

API
-------
You can only have one CapturePlus instance per page. The control is tied to your scope via the *capturePlus* directive and the *CapturePlus* service. The service will provide the default functionality for the CapturePlus control to run when one of the three methods are called. You can add functionaity to these methods using the service in your controller:

    var app = angular.module("testApp", ['CapturePlus']);

    app.controller('captureCtrl', function ($scope, CapturePlus) {
    
        CapturePlus.CapturePlusCallback = function (uid, response) {
            $scope.status = "Capture completed"
        }

        CapturePlus.CapturePlusStartTyping = function (uid, response) {
            $scope.status = "Typing";
        }

        CapturePlus.CapturePlusError = function (uid, response) {
            $scope.status = "Error";
        }
    });

The directive is used to identify where CapturePlus will insert the result so the service can update the controller:
`<input id="address" capture-plus ng-model="address" type="text" />`
