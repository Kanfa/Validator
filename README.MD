# Validator
Data validation based on rules

# Basic utilisation
```sh
$validator = new class extends \Validator\Core\AbstractValidator {
    public function __construct(?\Validator\Storage\MessageStorage $storage = null, \Noodlehaus\Config $config = null)
    {
        parent::__construct($storage, $config);
    }
};;

$validator->defineRules([
    'username' => 'max(50):min(4)',
    'other' => 'equals(username)'
]);

$data = ['username' => 'Kanfa', 'other' => 'Other'];

if ($validator->validate($data)) {
    // Action
} else {
    $errors = $validator->getErrors();
    // Error action
}
```