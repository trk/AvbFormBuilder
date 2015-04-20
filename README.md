AvbFormBuilder Module (Alti ve Bir Form Builder for ProcessWire)
====================================
### Module Author

* [İskender TOTOĞLU](http://www.altivebir.com.tr)

**Example Config File :**
```
$AvbFormBuilderForms = array(
    'contact' => array(
        'templates' => array(
            'form' => array(
                'wrapper' => array(
                    'tag' => 'div',
                    'attributes' => array(
                        'id' => 'contact-form'
                    )
                ),
                'attributes' => array(
                    'action' => wire('page')->url . '#contact-form',
                    'method' => 'post',
                    'data-role' => 'form'
                ),
                'template' => '{wrapper}{errors}{success}<form{attributes}>{fields}</form>{/wrapper}'
            ),
            'errors' => array(
                'wrapper' => array(
                    'tag' => 'div',
                    'attributes' => array(
                        'class' => 'alert alert-warning alert-dismissable'
                    )
                ),
                'title' => array(
                    'tag' => 'h4',
                    'attributes' => array(),
                    'content' => 'You have some errors, while trying to send form to us'
                ),
                'message' => array(
                    'tag' => 'p',
                    'attributes' => array(),
                    'content' => 'Please check the following errors...'
                ),
                'errors' => array(
                    'tag' => 'p',
                    'attributes' => array(),
                ),
                'template' => '{wrapper}<button type="button" class="close" data-dismiss="alert" aria-hidden="true">&times;</button>{title}<hr />{message}{errors}{/wrapper}'
            ),
            'success' => array(
                'wrapper' => array(
                    'tag' => 'div',
                    'attributes' => array(
                        'class' => 'alert alert-success alert-dismissable'
                    )
                ),
                'title' => array(
                    'tag' => 'h4',
                    'attributes' => array(),
                    'content' => 'Your form successfully sent'
                ),
                'message' => array(
                    'tag' => 'p',
                    'attributes' => array(),
                    'content' => 'Thanks you, for your interest'
                ),
                'template' => '{wrapper}<button type="button" class="close" data-dismiss="alert" aria-hidden="true">&times;</button>{title}<hr />{message}{/wrapper}'
            ),
            'row' => array(
                'tag' => 'div',
                'attributes' => array(
                    'class' => 'row'
                )
            ),
            'wrapper' => array(
                'tag' => 'div',
                'attributes' => array(
                    'class' => 'col-md-6'
                ),
                'template' => '{wrapper}<div class="form-group">{label}{input}</div>{/wrapper}',
            )
        ),
        'emailFrom' => 'no-reply@domain.ltd',
        'emails' => array
        (
            array
            (
                'to' => 'admin@domain.ltd',
                'subject' => 'You have a new message from contact form',
            ),
            array
            (
                'to::input' => 'email', // send secondary mail to user, use mail address from your form input field
                'subject' => 'Thanks you for your interest',
                'message' => 'When we receive your email, we will answer as soon as possible.'
            ) // You can add much more....
        ),
        'fields' => array
        (
            'firstname' => array(
                'label'     => __('First name'),
                'rule'      => 'required|max_len,20',
                'filter'    => 'sanitize_string',
                'type'      => 'text',
                'wrapper'   => array(
                    'attributes' => array(
                        'class' => 'col-lg-4'
                    )
                ),
                'attributes'=> array(
                    'class' => 'form-control'
                ),
                'rowStart'  => TRUE
            ),
            'lastname' => array(
                'label'     => __('Last name'),
                'rule'      => 'required|max_len,20',
                'filter'    => 'sanitize_string',
                'type'      => 'text',
                'wrapper'   => array(
                    'attributes' => array(
                        'class' => 'col-lg-4'
                    )
                ),
                'attributes'=> array(
                    'class' => 'form-control'
                )
            ),
            'email'	=> array(
                'label'     => __('Email Address'),
                'rule'      => 'required|valid_email',
                'filter'    => 'sanitize_string',
                'type'      => 'text',
                'wrapper'   => array(
                    'attributes' => array(
                        'class' => 'col-lg-4'
                    )
                ),
                'attributes'=> array(
                    'class' => 'form-control'
                ),
                'rowEnd'    => TRUE
            ),
            'subject' => array(
                'label'     => __('Subject'),
                'rule'      => 'required',
                'filter'    => 'sanitize_string',
                'type'      => 'text',
                'wrapper'   => array(
                    'attributes' => array(
                        'class' => 'col-lg-12'
                    )
                ),
                'attributes'=> array(
                    'class' => 'form-control'
                ),
                'rowStart'  => TRUE,
                'rowEnd'    => TRUE
            ),
            'message' => array(
                'label'     => __('Message'),
                'rule'      => 'required',
                'filter'    => 'sanitize_string',
                'type'      => 'textarea',
                'wrapper'   => array(
                    'attributes' => array(
                        'class' => 'col-lg-12'
                    )
                ),
                'attributes'=> array(
                    'class' => 'form-control',
                    'rows' => 6
                ),
                'rowStart'  => TRUE,
                'rowEnd'    => TRUE
            ),
            'submit' => array(
                'type' => 'button',
                'value' => $config->translations['button_send_email'],
                'wrapper'   => array(
                    'attributes' => array(
                        'class' => 'col-md-12'
                    ),
                    'template' => '{wrapper}<hr /><div class="form-group text-right">{label}{input}</div>{/wrapper}'
                ),
                'attributes' => array(
                    'class' => 'btn btn-normal'
                ),
                'email'     => FALSE,
                'rowStart'  => TRUE,
                'rowEnd'    => TRUE
            )
        )
    )
);
```