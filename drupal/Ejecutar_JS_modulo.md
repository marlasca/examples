# Ejecutar Javascript en un módulo de Drupal
Defino librería en el módulo:
XXX.libraries.yml
```
nombre-libreria:
  version: 1.x
  css:
    theme:
      css/nombre-libreria.css: {}
  js:
    js/nombre-libreria.js: {} {preprocess: false}
  dependencies:
    - core/jquery
    - core/drupal
```

Defino el javascript en la carpeta js, por ejemplo:
```
(function ($) {
	$(document).ready(function () {
		// When submitting the form, first open tabs with invalid fields.
		$('.node-qat-form #edit-submit').click(function() {
		  $('input:invalid').each(function() {
		    const paneId = $(this).closest('.vertical-tabs-pane').attr('id');
		    const paneLink = $('a[href="#' + paneId + '"]');
		    paneLink.click();
		  });
		});
	});
})(jQuery);
```

Cargo la librería desde el módulo (XXX.module) cuando me convenga, por ejemplo, cuando relleno un formulario de tipo content-type = 'qat'
```
function project512_form_alter(&$form, \Drupal\Core\Form\FormStateInterface $form_state, $form_id) {
  $formObject = $form_state->getFormObject();
  if ($formObject instanceof \Drupal\Core\Entity\EntityFormInterface) {
    $entity = $formObject->getEntity();
    if ( $entity->getEntityTypeId() === 'node' && in_array($entity->bundle(), ['qat'])) {
      $form['#attached']['library'][] = 'project512/field_group_512';
    }
  }
}
```
